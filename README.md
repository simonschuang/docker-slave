Jenkins Agent Docker image
===

[![Docker Stars](https://img.shields.io/docker/stars/jenkinsci/slave.svg)](https://hub.docker.com/r/jenkinsci/slave/)
[![Docker Pulls](https://img.shields.io/docker/pulls/jenkinsci/slave.svg)](https://hub.docker.com/r/jenkinsci/slave/)
[![Docker Automated build](https://img.shields.io/docker/automated/jenkinsci/slave.svg)](https://hub.docker.com/r/jenkinsci/slave/)

This is a base image for Docker, which includes OpenJDK 8 and the Jenkins agent executable (slave.jar).
This executable is an instance of the [Jenkins Remoting library](https://github.com/jenkinsci/remoting).

## Usage

This image is used as the basis for the [Docker JNLP Agent](https://github.com/jenkinsci/docker-jnlp-slave/) image.
In that image, the container is launched externally and attaches to Jenkins.

This image may instead be used to launch an agent using the **Launch method** of **Launch agent via execution of command on the master**. Try for example

```sh
docker run -i --rm --name agent jenkinsci/slave:3.7-1 java -jar /usr/share/jenkins/slave.jar
```

after setting **Remote root directory** to `/home/jenkins`.

## Configurations

The image has several supported configurations, which can be accessed via the following tags:

* `latest`: Latest version with the newest remoting (based on `openjdk:8-jdk`)
* `alpine`: Small image based on Alpine Linux (based on `openjdk:8-jdk-alpine`)
* `2.62`: This version bundles [Remoting 2.x](https://github.com/jenkinsci/remoting#remoting-2]), which is compatible with Jenkins servers running on Java 6 (`1.609.4` and below)
* `2.62-alpine`: Small image with Remoting 2.x
