# web-service-gin

Developing a RESTful API with Go and Gin with reference to the official Go tutorial.

## Design API endpoints.

```
/albums
    - GET – Get a list of all albums, returned as JSON.
    - POST – Add a new album from request data sent as JSON.
/albums/:id
    - GET – Get an album by its ID, returning the album data as JSON.
```

### Parameters in path

gin can easily accept parameters in the path such as `/:id`.

## Create the data.

```Go
// album represents data about a record album.
type album struct {
    ID     string  `json:"id"`
    Title  string  `json:"title"`
    Artist string  `json:"artist"`
    Price  float64 `json:"price"`
}
```

## Write a handler

```Go
func main() {
    router := gin.Default()
    router.GET("/albums", getAlbums)
    router.GET("/albums/:id", getAlbumByID)
    router.POST("/albums", postAlbums)

    router.Run("localhost:8080")
}
```

## Try HTTP request with curl command

### GET – Get a list of all albums, returned as JSON.
```
$ curl http://localhost:8080/albums
```

### POST – Add a new album from request data sent as JSON.
```
$ curl http://localhost:8080/albums \
    --include \
    --header "Content-Type: application/json" \
    --request "POST" \
    --data '{"id": "4","title": "The Modern Sound of Betty Carter","artist": "Betty Carter","price": 49.99}'
```

### GET – Get an album by its ID, returning the album data as JSON.
```
$ curl http://localhost:8080/albums/2
```


## References

[Tutorial: Developing a RESTful API with Go and Gin](https://go.dev/doc/tutorial/web-service-gin)
