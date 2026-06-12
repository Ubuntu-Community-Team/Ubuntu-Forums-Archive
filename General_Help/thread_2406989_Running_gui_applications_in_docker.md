---
title: "Running gui applications in docker?"
date: 2018-11-28
forum: General Help
---

### Post by peterandersson on 2018-11-28
I just installed a ubuntu installation with the mini.iso.
Then i installed docker-cd, now I'm wondering what are the absolute minimum packages i need to install to run gui applications in docker, example: 
[https://medium.com/@SaravSun/running-gui-applications-inside-docker-containers-83d65c0db110](https://medium.com/@SaravSun/running-gui-applications-inside-docker-containers-83d65c0db110)
[http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/)

I want the applications to run in fullscreen.

I have done the following
* Installed ubuntu with mini.iso
* Installed docker [https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1)
* Installed xserver `sudo apt-get install xauth xorg xinit xserver-xorg-core xserver-xorg xserver-common`.
Created and build the following docker image
```
FROM ubuntu:14.04


RUN apt-get update && apt-get install -y firefox


# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer


USER developer
ENV HOME /home/developer
CMD /usr/bin/firefox
```

then tried to run it with 
```
docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix firefox
```
but i get the following error:

```
error: XDG_RUNTIME_DIR not set in the enviorment.
Error: cannot open display:
```

What am i doing wrong?

---

