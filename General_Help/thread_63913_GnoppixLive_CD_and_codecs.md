---
title: "Gnoppix/Live CD and codecs"
date: 2005-09-09
forum: General Help
---

### Post by graabein on 2005-09-09
Hi, I want to listen to my mp3s and watch some movies from a Live CD. Can I just follow the starter guide for downloading codecs? I tried [How to install Multimedia Codecs](http://ubuntuguide.org/#codecs) and it went well until:

```
ubuntu@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install libdivx4linux
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
```

I tried this with both Breezy and Hoary repos... The mp3s are okay but I only get sound and no picture with avi/mpg movies in Totem.

The Live CD I'm running is Gnoppix 2.12 beta1 btw.

---

### Post by rafakl on 2005-09-09
Did you add the backports at the end of your sources.list??

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by graabein on 2005-09-09
Brilliant. I thought the codecs were part of multi/universe. But I still don't get no picture in Totem though... Could it be my graphics card?



Edit: I followed the instructions for DVD playback and xine and I can at least watch divx with xine now.

---

### Post by rafakl on 2005-09-10
and what about dvd's??

---

### Post by graabein on 2005-09-27
When I run the Live CD I have not tried removing the disc to play a DVD...

---

### Post by floyd27 on 2005-10-04
you cant...unless yo have another drive

---

### Post by graabein on 2005-10-05
What I'd like to know is why the entire disc (live cd) is not read to memory when I've got 1gb ram... anyone care to share?

---

