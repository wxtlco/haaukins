# go-ntp
The component responsible for managing the NTP.

## How to run
First, install dependencies (requiring `go 1.7` or higher):
```
go get ./...
```

Then, run the following to setup a complete event (i.e. the complete set of components, including CTFd, Guacamole, and a set of labs),
```
go run app/app.go
```

### Customizing an event
As of now, there are two configuration files (located in `app`):
- `config.yml` for the configuration of CTFd, Guacamole and nginx
- `exercises.yml` for the configuration of the exercises, including the docker configuration, the flag

### Registry authentication
We run a private Docker repository where most of the images needed for the exercises reside.
In order to pull new images and newer versions from this repository, `app.go` needs credentials to login.

As of now, running `app/app.go` requires the existence of an `auth.json` file in the root of the project,
containing the authentication needed for pulling Docker images from a private repository.
The file should look like:
```
{
  "username": "<username>",
  "password": "<password",
  "serveraddress": "<registry address>"
}
```