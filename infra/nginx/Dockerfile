FROM node:14-alpine as node
FROM nginx:1.20-alpine
LABEL maintainer="soregashi-27"
SHELL ["/bin/ash", "-ouex", "pipefail", "-c"]

ENV TZ=UTC

RUN apk update && \
  apk add --update --no--cache --virtual=.build-dependencies g++

# node command
COPY --from=node /usr/local/bin /usr/local/bin
# npm command
COPY --from=node /usr/local/lib /usr/local/lib
#yarn command
COPY --from=node /opt /opt
#nginx config file
COPY ./infra/docker/nginx/*.conf /etc/nginx/conf.d/

WORKDIR /work