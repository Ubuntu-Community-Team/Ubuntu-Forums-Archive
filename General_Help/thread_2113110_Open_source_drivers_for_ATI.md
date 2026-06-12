---
title: "Open source drivers for ATI"
date: 2013-02-06
forum: General Help
---

### Post by Moofy on 2013-02-06
I ran into some problems trying to install the open source drivers to make my 3D acceleration better, since Cinnamon seems to be a little bit laggy with the animation for me.
I use ATI Radeon HD 5670.

[I followed this guide. ]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx")
I got to command line 2, and this occured:
```
mathias@mucap:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-modaliases is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  fglrx-updates:i386 fglrx-experimental-9:i386 fglrx:i386 fglrx-updates
  fglrx-experimental-9 fglrx

E: Package 'fglrx-modaliases' has no installation candidate
```

---

### Post by efflandt on 2013-02-06
Why would you try to install fglrx-modaliases without installing fglrx (ie, when you have no fglrx modules)? Is there some reason you do not want to install fglrx accelerated video, or does it not support your chip?

---

### Post by Yellow Pasque on 2013-02-06
The open-source drivers are installed by default, so you don't have to do anything.
fglrx-modaliases package is no longer used in Ubuntu, so the document is out of date.

---

### Post by Yellow Pasque on 2013-02-06
Okay, I have updated the document. That said, the document is for people who installed fglrx/Catalyst and now want to go back to the open-source/default driver. I'm not sure if that applies to your situation. Have you tried installing fglrx/Catalyst?

What is the output of glxinfo?
```
sudo apt-get install mesa-utils
glxinfo
```

---

