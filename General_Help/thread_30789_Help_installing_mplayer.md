---
title: "Help installing mplayer"
date: 2005-04-30
forum: General Help
---

### Post by momo66 on 2005-04-30
New to Ubuntu and have gone through the startup guide with a lot of success.  Have almost everything working I was using on Windows.

Cannot get mplayer installed.  This is the last few lines of the apt-get for mplayer

> Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse mplayer-386 1:1.0-pre6-0.3ubuntu6 [3583kB]
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter


Its asking for the cd.  Any ideas on what I need to do?

momo

---

### Post by DutchLau on 2005-04-30
Hi,

Take a look at this: [http://www.ubuntuguide.org/#mplayer](http://www.ubuntuguide.org/#mplayer)     Follow the steps and you will install Mplayer easily and cleanly. There are also better (don't bash at me for this) video players out there, but I still use Mplayer for videos within FireFox. You should also give VLC (sudo apt-get install vlc), Gxine (sudo apt-get install gxine) and some others ago. Scrap Totem though, this hasn't worked with me and many others from the start!

Good luck with your installation,

Let us know if it worked,

DutchLau

---

### Post by cutOff on 2005-04-30
Edit the file sources.list placed in /etc/apt and comment (#) the line referred to your Cdrom.

Here my sources.list

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://es.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://es.archive.ubuntu.com/ubuntu hoary main restricted

#deb http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://es.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://es.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

##Marillat
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

##backports
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
```

---

### Post by momo66 on 2005-04-30
Thanks!!  that was my problem.

---

### Post by sebastyan on 2005-05-30
Hy it is asking to insert the CD from where you install Ubuntu Linux for the first time.
You can also download Unofficial Ubuntu Addon_CD where you can find MPLayer too!
For me it worked just fine 
Try this links
  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
  [http://ubuntuguide.org/add-on-cd](http://ubuntuguide.org/add-on-cd)

---

