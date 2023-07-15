# baradb-http

baradb-http is a simple web service that integrates HTTP into [baradb](https://github.com/saint-yellow/baradb), a key/value storage engine.

It uses web framework [gin](https://github.com/gin-gonic/gin)
## Install

```shell 
$ go get -u github.com/saint-yellow/baradb-http
```

Executing this command will add a binary file callled `baradb-http` to your `${GOPATH}/bin`

## APIs 

Use the exposed web APIs shown below to access the storage engine.

|HTTP Method|Route|Description|
|---|---|---|
|GET|/baradb/keys|Get all keys|
|POST|/baradb|Append a key/value pair|
|DELETE|/baradb/:key|Delete a key/value pair by the given key|
|GET|/baradb/:key|Get the value of the given key|
|GET|/baradb/stat|Get the statistical information|

## Usage

Suppose the `${GOPATH}/bin/baradb-http` is in your `${PATH}`, you can use it like this:

```console
$ baradb-http &

$ curl http://localhost:8080/baradb/stat
{"success":true,"message":"ok","data":"keyNumber":0,"dataFileNumber":0,"reclaimableSize":0,"diskSize":0}%

$ curl -X POST -d '{"key":"key001","value":"value001"}' http://localhost:8080/baradb/
{"success":true,"message":"ok"}%

$ curl http://localhost:8080/baradb/keys
{"success":true,"message":"ok","data":["key001"]}%

$ curl http://localhost:8080/baradb/key001
{"success":true,"message":"ok","data":"value001"}%

$ curl -X DELETE http://localhost:8080/baradb/key001
{"success":true,"message":"ok"}%
```

## Contributing

PRs accepted.

## License

MIT © Saint-Yellow 
