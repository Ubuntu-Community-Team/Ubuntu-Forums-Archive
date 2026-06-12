---
title: "Unmet dependencies problem"
date: 2015-02-21
forum: General Help
---

### Post by iason2 on 2015-02-21
Hello everyone. I have downloaded some C++ libraries and I can't run them because I am missing GL/glu.h. Apparently if I install freeglut3 and freeglut3-dev, that would solve the problem, but when I try to install freeglut3-dev I get unmet dependencies error. It is the same if I try to install [COLOR=#000000] libglu1-mesa-dev, which has the glu.h file that I need. This is the error I get:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                          Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
                  Depends: gstreamer1.0-clutter but it is not going to be installed
libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                         Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I have also tried sudo apt-get -f install but the problem persists. I am a complete Linux newbie, only installed them yesterday, so there's a lot of stuff I don't know here.

---

### Post by mc4man on 2015-02-21
what do these do?
```
sudo apt-get update
```
```
sudo apt-get install libglu1-mesa-dev
```

---

### Post by iason2 on 2015-02-22
Sorry for the late reply, but Im having other problems now as well. I was able to bypass the problem of my first post by sudo apt-get purge some packages, then installing freeglut3 and freeglut3-dev correctly. But for some reason whenever I start the virtual machine now (I'm using virtualbox) I only get a black screen, no desktop or anything.
I tried reinstalling Ubuntu but the same thing happened. Anyone have an idea why? I don't think this has anything to with me purging the package ( I only purged libcheese-gtk23 by the way).

---

### Post by mc4man on 2015-02-22
Not sure where to begin now - in any event removing libcheese-gtk23 was a very poor idea. It would of removed & installed a number of packages, nothing good for 14.04, assuming you used Ubuntu 14.04 

To further complicate things  14.04.2 just released. I'm thinking you used that image. Unfortunately 14.04.2 will not allow the full range of -dev packages that 14.04 release or 14.04.1 will. As it happens freeglut3-dev is one of those packages. 

So I suggest starting over & use this image instead - 
[http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)

scroll down & look for either ubuntu-14.04.1-desktop-amd64.iso or ubuntu-14.04.1-desktop-i386.iso
After installing run sudo apt-get update then install whatever you wish.
Do not down the road do an install/upgrade of the lts-utopic, lts-vivid, lts-whatever mesa packages (you would need to explicitly do so may never come up

bug for anyone interested
[https://bugs.launchpad.net/ubuntu/+source/freeglut/+bug/1424466](https://bugs.launchpad.net/ubuntu/+source/freeglut/+bug/1424466)

---

### Post by iason2 on 2015-02-23
You are right, 14.04.2 is indeed the one I used. Your answer clarifies things a lot, thank you. I will try with the new image and report results this evening.

---

### Post by nmi2 on 2015-03-10
I had the same problem in Ubuntu 14.04.2 trying to install qtcreator. Also trying to install Qt4/5 development packages such as qt4-default and qt5-default would have downgraded the whole X.org to the original trusty version instead of lts-utopic.

This dependency mess is somehow connected to the new Mesa packages, and [can be fixed by manually installing lts-utopic versions]("http://answers.ros.org/question/203610/ubuntu-14042-unmet-dependencies/?answer=203724#post-id-203724"). I installed these packages:
```
sudo apt-get install xserver-xorg-dev-lts-utopic mesa-common-dev-lts-utopic libgles2-mesa-dev-lts-utopic libgles1-mesa-dev-lts-utopic libgl1-mesa-dev-lts-utopic libegl1-mesa-dev-lts-utopic
```

---

### Post by mkim3 on 2015-03-12
> **nmi2 said:**
> I had the same problem in Ubuntu 14.04.2 trying to install qtcreator. Also trying to install Qt4/5 development packages such as qt4-default and qt5-default would have downgraded the whole X.org to the original trusty version instead of lts-utopic.

This dependency mess is somehow connected to the new Mesa packages, and [can be fixed by manually installing lts-utopic versions]("http://answers.ros.org/question/203610/ubuntu-14042-unmet-dependencies/?answer=203724#post-id-203724"). I installed these packages:
```
sudo apt-get install xserver-xorg-dev-lts-utopic mesa-common-dev-lts-utopic libgles2-mesa-dev-lts-utopic libgles1-mesa-dev-lts-utopic libgl1-mesa-dev-lts-utopic libegl1-mesa-dev-lts-utopic
```

Thank you, I was having the same problems with 14.04.2 and unmet dependencies. The link fixed my problems.  :)

---

### Post by Weicheng_Zhu on 2015-03-17
Hi,
I installed Ubuntu 14.04.2 yesterday and I met exactly the same problem as yours.
This problem is solved by changing another mirror.
Hope it can help you too:)

---

