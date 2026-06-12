---
title: "Settings crashes system after sudo apt autoremove - log included"
date: 2020-02-09
forum: General Help
---

### Post by entheopsybin on 2020-02-09
Hi, i am currently running Ubuntu 18.04 alongside Windows 10 with the Unity desktop environment.
Terminal said i should type either sudo apt autoremove or sudo apt-get autoremove when i typed sudo apt upgrade and sudo apt-get upgrade. (i forgot whether it asked to type sudo apt-get autoremove or sudo apt autoremove)
Ive had Ubuntu break from this command many times, and i thought i might as well trust it on this occasion not having done it in a while and what a mistake that was, now when opening either gnome-control-center and unity-control-center they fail to open and my system freezes then powers off.
Here is what the command removed:

                        Commandline: apt autoremove
 Requested-By: sam (1000)
 Remove: libportmidi0:amd64 (1:217-6), libxdmcp6:i386 (1:1.1.2-3), libdrm-nouveau2:i386 (2.4.99-1ubuntu1~18.04.2), libnvidia-compute-435:i386 (435.21-0ubuntu0.18.04.2), libllvm9:i386 (1:9-2~ubuntu18.04.2), libportaudio2:amd64 (19.6.0-1), libnvidia-encode-435:i386 (435.21-0ubuntu0.18.04.2), nvidia-kernel-common-435:amd64 (435.21-0ubuntu0.18.04.2), libnvidia-gl-435:i386 (435.21-0ubuntu0.18.04.2), libpciaccess0:i386 (0.14-1), libxcb-present0:i386 (1.13-2~ubuntu18.04), libgl1:i386 (1.0.0-2ubuntu2.3), libglapi-mesa:i386 (19.2.8-0ubuntu0~18.04.2), libnvidia-fbc1-435:i386 (435.21-0ubuntu0.18.04.2), libelf1:i386 (0.170-0.4ubuntu0.1), libnvidia-decode-435:i386 (435.21-0ubuntu0.18.04.2), libbsd0:i386 (0.8.7-1ubuntu0.1), libvamp-sdk2v5:amd64 (2.7.1~repack0-1), libid3tag0:amd64 (0.15.1b-13), mixxx-data:amd64 (2.0.0~dfsg-9), libx11-6:i386 (2:1.6.4-3ubuntu0.2), nvidia-prime:amd64 (0.8.8.2), libexpat1:i386 (2.2.5-3ubuntu0.2), libvamp-hostsdk3v5:amd64 (2.7.1~repack0-1), libxshmfence1:i386 (1.3-1), libqt5concurrent5:amd64 (5.9.5+dfsg-0ubuntu2.4), libdrm-amdgpu1:i386 (2.4.99-1ubuntu1~18.04.2), libhidapi-libusb0:amd64 (0.8.0~rc1+git20140818.d17db57+dfsg-2), libxau6:i386 (1:1.0.8-1), libxcb1:i386 (1.13-2~ubuntu18.04), pkg-config:amd64 (0.29.1-0ubuntu2), libxinerama1:i386 (2:1.1.3-1), libsoundtouch1:amd64 (1.9.2-3), libopusfile0:amd64 (0.9+20170913-1build1), libdrm2:i386 (2.4.99-1ubuntu1~18.04.2), libnvidia-ifr1-435:i386 (435.21-0ubuntu0.18.04.2), libglx0:i386 (1.0.0-2ubuntu2.3), libxfixes3:i386 (1:5.0.3-1), libgl1-mesa-dri:i386 (19.2.8-0ubuntu0~18.04.2), libxxf86vm1:i386 (1:1.1.4-1), screen-resolution-extra:amd64 (0.17.3), libxdamage1:i386 (1:1.1.4-3), libgl1-mesa-glx:i386 (19.2.8-0ubuntu0~18.04.2), libedit2:i386 (3.1-20170329-1), libdrm-intel1:i386 (2.4.99-1ubuntu1~18.04.2), libqt5scripttools5:amd64 (5.9.5+dfsg-0ubuntu1), libffi6:i386 (3.2.1-8), libnvidia-common-435:amd64 (435.21-0ubuntu0.18.04.2), libdrm-radeon1:i386 (2.4.99-1ubuntu1~18.04.2), libatomic1:i386 (8.3.0-6ubuntu1~18.04.1), libstdc++6:i386 (8.3.0-6ubuntu1~18.04.1), libxcb-glx0:i386 (1.13-2~ubuntu18.04), libxss1:i386 (1:1.2.2-1), libxcb-dri2-0:i386 (1.13-2~ubuntu18.04), libsensors4:i386 (1:3.4.0-4), libxcb-dri3-0:i386 (1.13-2~ubuntu18.04), libx11-xcb1:i386 (2:1.6.4-3ubuntu0.2), libxcb-sync1:i386 (1.13-2~ubuntu18.04), nvidia-settings:amd64 (390.77-0ubuntu0.18.04.1), libxext6:i386 (2:1.3.3-1), libglx-mesa0:i386 (19.2.8-0ubuntu0~18.04.2), libglvnd0:i386 (1.0.0-2ubuntu2.3)

Ive tried purging them and then using apt autoremove then reinstalling like this:

sudo apt-get remove unity-control-center 
sudo apt autoremove
sudo apt-get install unity-control-center

sudo apt-get remove gnome-control-center 
sudo apt autoremove
sudo apt-get install gnome-control-center

Is it because i typed sudo apt autoremove instead of sudo apt-get autoremove?

Plus ive thought of reinstalling all the packages or finding out which ones affected what but will have to remove all the brackets, is there another way around all this?

---

