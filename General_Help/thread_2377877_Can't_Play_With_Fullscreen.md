---
title: "Can't Play With Fullscreen"
date: 2017-11-17
forum: General Help
---

### Post by hazard-droid on 2017-11-17
[COLOR=#000000]When I Play Some Video On Youtube On Fullscreen mode it works great but when I exit The Video it Gets Stuck On The Screen (Like a Picture) The Unity Menu Disappears and The Menu On The Left Also Disappears And If I'm Some Game on fullscreen same problem to use my pc I Have To Restart it.



I'm using ubuntu 16.04.3 LTS




[/COLOR]

---

### Post by pissedoffdude on 2017-11-17
Let's find out your Ubuntu version and whether or not you have the proper drivers installed (this could also possibly be related to wayland if you're on the latest Ubuntu)

1) Can you get the output of```
cat /etc/lsb-release
```
2) Let's see if you're running wayland:
```
echo $XDG_SESSION_TYPE

```
3) Let's ensure you have proprietary drivers installed:
```
sudo ubuntu-drivers autoinstall 

```

Note: if 3 installs a few packages, you should reboot afterwards and try the full screen video again.

---

### Post by monkeybrain20122 on 2017-11-17
Which games and what is your graphic card? What is the output of
```
glxinfo| grep OpenGL 
```

I have exactly the same problem with supertuxkart0.92 on mesa 17.2. Fixed by compiling the developmental version of STK from source (installing from ppa didn't fix it)

---

### Post by hazard-droid on 2017-11-17
I Got This Output After sudo ubuntu-drivers autoinstall


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei game-data-packager
  icoutils ioquake3 ioquake3-server libcapi20-3 libfdk-aac0 libgif7
  libmagick++-6.q16-5v5 libodbc1 libopusfile0 libosmesa6 libxcb-xinerama0
  libxml++2.6-2v5 odbcinst odbcinst1debian2 p7zip ppsspp-common python3-yaml
  supertuxkart-data synfig-examples ttf-wqy-microhei unixodbc wine-gecko2.21
  wine-mono0.0.8 yamagi-quake2 yamagi-quake2-core
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by hazard-droid on 2017-11-17
> **pissedoffdude said:**
> Let's find out your Ubuntu version and whether or not you have the proper drivers installed (this could also possibly be related to wayland if you're on the latest Ubuntu)

1) Can you get the output of```
cat /etc/lsb-release
```
2) Let's see if you're running wayland:
```
echo $XDG_SESSION_TYPE

```
3) Let's ensure you have proprietary drivers installed:
```
sudo ubuntu-drivers autoinstall 

```

Note: if 3 installs a few packages, you should reboot afterwards and try the full screen video again.

**It didn't worked bro **

---

