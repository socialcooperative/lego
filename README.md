# social.coop lego

# Docker Alpine Ruby container

A small Docker image with Alphine 3.3 and Ruby.

## Usage

Install [Docker](https://docs.docker.com/engine/installation/).

To build an image from the `Dockerfile` run:

    $ make build
    $ docker images

    REPOSITORY           TAG                 IMAGE ID            CREATED             SIZE
    docker-alpine-ruby   latest              1fa6b8033680        7 seconds ago       31.72 MB
    alpine               3.4                 4e38e38c8ce0        8 weeks ago         4.799 MB

Now you can test your image by running a command:

    $ make execute COMMAND='ruby -v'

    ruby 2.3.1p112 (2016-04-26 revision 54768) [x86_64-linux-musl]

Or you can connect in console:

    $ make sh

    / # ruby -v
    ruby 2.3.1p112 (2016-04-26 revision 54768) [x86_64-linux-musl]

To reduce the size of the image:

    $ make flatten

    REPOSITORY           TAG                 IMAGE ID            CREATED             SIZE
    docker-alpine-ruby   latest              aaad6c488c79        8 seconds ago       29.24 MB
    <none>               <none>              1fa6b8033680        3 minutes ago       31.93 MB
    alpine               3.4                 4e38e38c8ce0        8 weeks ago         4.799 MB

Remove containers and images:

    $ docker ps -a

    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
    c20ce0f07d47        1fa6b8033680        "/bin/sh"           2 minutes ago       Created                                 docker-alpine-ruby

    $ make remove_all_containers
    $ make remove_all_images

## Native extensions

Add required packages or gems from the [package repository](http://pkgs.alpinelinux.org/packages) to the RUBY_PACKAGES line of the Dockerfile.
