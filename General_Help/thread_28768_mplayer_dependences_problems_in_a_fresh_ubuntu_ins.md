---
title: "mplayer dependences problems in a fresh ubuntu installation"
date: 2005-04-21
forum: General Help
---

### Post by T31 on 2005-04-21
I have done a full fresh installation of ubuntu and I met this :( trying to install the k6 mplayer version, note I have a amd box

mplayer-k6:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: xmms but it is not going to be installed

I just installed java azureus, thunderbird w32codecs gstream and skype packages

please help

thx in advance

---

### Post by Fab on 2005-04-21
disable the marillat repos if  you have them enabled.. the mplayer packages their are newer and have dependencies that ubuntu repos dont meet (because of the backporting policy i think)

---

### Post by T31 on 2005-04-21
now it is installed...

but doesnt play anything

 ](*,)

---

### Post by NeoChaosX on 2005-04-21
What do you mean it doesn't play anything? Does the program lock up when you try to play a video or something?

---

### Post by T31 on 2005-04-22
yes, sorry u r right, i have to use kill to finish it

and when i try to use the mozilla firefox plugin loads till the 25% and then lock up as well :(

---

### Post by T31 on 2005-04-23
Well, I fixed but now Im not sure if it was becouse I uninstalled the package mplayer-k6 and installed instead the package 386 or becouse I eliminated the daemon esd from my system

anyway thx a lot to everyone was helping xDDD

---

