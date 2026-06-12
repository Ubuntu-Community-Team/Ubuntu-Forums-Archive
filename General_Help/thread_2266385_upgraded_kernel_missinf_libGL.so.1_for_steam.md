---
title: "upgraded kernel missinf libGL.so.1 for steam"
date: 2015-02-22
forum: General Help
---

### Post by grier-devon on 2015-02-22
Hey Ubuntu Community,
So I wanted to run the 3.16 kernel with Ubuntu 14.04.2, my laptop came with Ubuntu 14.04.1 and I read that all new installed of Ubuntu will come with 3.16 kernel but everyone upgrading from 14.04.1 to 14.04.2 will remain on 3.13 kernel. So I went to this guide to upgrade to the 3.16 kernel.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

I installed the new kernel with these commands

```
[COLOR=#333333][FONT=monospace]sudo apt-get install linux-generic-lts-utopic xserver-xorg-lts-utopic libegl1-mesa-drivers-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-input-all-lts-utopic
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sudo apt-get install linux-signed-generic-lts-utopic[/FONT][/COLOR]
```

Everything has been fine since the upgrade and a quick "uname -r" and the output is "3.16.0-30-generic", when I go to run steam I get this error...

```
You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1
```

So I google the error and everywhere I look everyone is complaining about this issue the with nvidia mesa libs (my graphics is the intel iris pro 5200), but everyone said this is missing and I ran this....
```
devon@MrUbuntu:~$ sudo apt-get install libgl1-mesa-glx:i386[sudo] password for devon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

All I can say at this point is please help and any help would be appreciated. Thanks

EDIT: I ran the steam client again and it had me run this and this is how it fails
```
devon@MrUbuntu:~$ sudo apt-get install libgl1-mesa-glx:i386[sudo] password for devon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by mc4man on 2015-02-22
Try this ( a simulation), if good then remove the -s option to do for real
```
 sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386
```

---

### Post by grier-devon on 2015-02-22
So I ran what you said and got
```
devon@MrUbuntu:~$ sudo apt-get -s install libgl1-mesa-glx-lts-utopic:i386[sudo] password for devon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386
  libelf1:i386 libgl1-mesa-dri-lts-utopic:i386 libglapi-mesa-lts-utopic:i386
  libllvm3.5:i386 libpciaccess0:i386 libtxc-dxtn-s2tc0:i386 libx11-xcb1:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxshmfence1:i386 libxxf86vm1:i386
The following NEW packages will be installed:
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libedit2:i386
  libelf1:i386 libgl1-mesa-dri-lts-utopic:i386 libgl1-mesa-glx-lts-utopic:i386
  libglapi-mesa-lts-utopic:i386 libllvm3.5:i386 libpciaccess0:i386
  libtxc-dxtn-s2tc0:i386 libx11-xcb1:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxshmfence1:i386 libxxf86vm1:i386
0 upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Inst libedit2:i386 (3.1-20130712-2 Ubuntu:14.04/trusty [i386])
Inst libelf1:i386 (0.158-0ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Inst libpciaccess0:i386 (0.13.2-1 Ubuntu:14.04/trusty [i386])
Inst libdrm-intel1:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libdrm-nouveau2:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libdrm-radeon1:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Inst libllvm3.5:i386 (1:3.5-4ubuntu2~trusty2 Ubuntu:14.04/trusty-updates [i386])
Inst libgl1-mesa-dri-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Inst libglapi-mesa-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Inst libx11-xcb1:i386 (2:1.6.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libxcb-dri2-0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxcb-dri3-0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxcb-glx0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxcb-present0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxcb-sync1:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxshmfence1:i386 (1.1-2 Ubuntu:14.04/trusty [i386])
Inst libxxf86vm1:i386 (1:1.1.3-1 Ubuntu:14.04/trusty [i386])
Inst libgl1-mesa-glx-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Inst libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1 Ubuntu:14.04/trusty [i386])
Conf libedit2:i386 (3.1-20130712-2 Ubuntu:14.04/trusty [i386])
Conf libelf1:i386 (0.158-0ubuntu5.2 Ubuntu:14.04/trusty-updates [i386])
Conf libpciaccess0:i386 (0.13.2-1 Ubuntu:14.04/trusty [i386])
Conf libdrm-intel1:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libdrm-nouveau2:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libdrm-radeon1:i386 (2.4.56-1~ubuntu2 Ubuntu:14.04/trusty-updates [i386])
Conf libllvm3.5:i386 (1:3.5-4ubuntu2~trusty2 Ubuntu:14.04/trusty-updates [i386])
Conf libgl1-mesa-dri-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Conf libglapi-mesa-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Conf libx11-xcb1:i386 (2:1.6.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libxcb-dri2-0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxcb-dri3-0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxcb-glx0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxcb-present0:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxcb-sync1:i386 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxshmfence1:i386 (1.1-2 Ubuntu:14.04/trusty [i386])
Conf libxxf86vm1:i386 (1:1.1.3-1 Ubuntu:14.04/trusty [i386])
Conf libgl1-mesa-glx-lts-utopic:i386 (10.3.2-0ubuntu1~trusty2 Ubuntu:14.04/trusty-updates [i386])
Conf libtxc-dxtn-s2tc0:i386 (0~git20131104-1.1 Ubuntu:14.04/trusty [i386])
```

Then when I try to open the steam client I get
```
Steam needs to install these additional packages: 	libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for devon: 
............................................................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by mc4man on 2015-02-22
As mentioned the command I gave you is a simulation, as in nothing was changed. So run the command again but remove the -s, like - 
```
sudo apt-get  install libgl1-mesa-glx-lts-utopic:i386
```

---

### Post by grier-devon on 2015-02-22
Thank you so much, working like a charm now.

---

### Post by szemy on 2015-02-25
Thanks so much!

---

