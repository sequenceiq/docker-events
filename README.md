When performing Docker trainings I like to show the Docker events stream.
This container is a **one-liner** to be able to watch docker events.

## Usage


```
$(docker run sequenceiq/docker-events)
```

## tl;dr

In the background what it does:

- starts a **socat** to proxy to make /var/run/docker.sock available as a usual tcp port.
- start **curl** to connect to docker daemon via the proxied docker.sock
- let **jq** format and colorize the json stream

## security

The socat trick makes it easy to reach the docker daemon via a tcp port, but removes
any SSL layer. So don’t expose the port proxied by socat.

