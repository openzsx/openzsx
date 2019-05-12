# Docker Tags, Registries, and User Identity
I’ve been spending a good deal of time recently building Docker images, and
pushing them around between development and deployment environments. The Docker
command line interface can feel awkward, and in some cases, confusing until you
really understand what’s going on. While Docker’s tutorial is good, the command
documentation often left me asking _**why ...**_

[docker tag](./images/docker_tag.jpg)

As I’ve become a more capable Docker user, I’ve gained respect for the depth of
function that can be expressed through this interface.

## Image Registries
Say you’ve created an image and are ready to share it. The most common way to do
this is to push it to a registry, from which you or others can pull it to a
target machine for deployment.

Registries can either be secure (login required), or insecure (no login required).
The default registry is Docker’s [index.docker.io](https://hub.docker.com/) (a.k.a.
Dockerhub). You can also set up your own private secure/insecure registries and
push or pull your images to/from multiple locations. This is handy for complex
environments where you may be developing for multiple platforms, or need to
deploy across an enterprise.

Specifying the destination or source registry of your image, along with other
image characteristics when you want to push/pull it is accomplished through
_tagging_.

## Image Tagging
Docker image tags are metadata strings that include multiple sets of information.
The Docker tag command is described as:

```
Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
```

Referring to a tag as ```TARGET_IMAGE``` made me first think that it was
creating a copy of a source image to generate a new target image. Reading more
closely, the tag command is logically binding metadata represented by the tag
string to the ```SOURCE_IMAGE``` so that Docker knows how to respond to user
requests from the command line interface.

### Anatomy of an Image Tag
A conventional image tag has a schema like this:

```
<registry>/<repository>:<version>
```
