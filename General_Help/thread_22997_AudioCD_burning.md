---
title: "AudioCD burning"
date: 2005-03-30
forum: General Help
---

### Post by irad on 2005-03-30
Last night I was sitting trying to download some programs that will burn audio cd
(Mp3 --> CD), but I failed.
I also tried to download k3b, but it didn't recognize those mp3 files, and I don't know why,

Is there any program that can burn mp3 files into audio CD?

---

### Post by fdoving on 2005-03-30
[QUOTE=irad]Last night I was sitting trying to download some programs that will burn audio cd
(Mp3 --> CD), but I failed.
I also tried to download k3b, but it didn't recognize those mp3 files, and I don't know why,

Is there any program that can burn mp3 files into audio CD?[/QUOTE]
 I use k3b, works like a charm. Other programs you can checkout is arson and gnomebaker.

---

### Post by ubuntu_demon on 2005-03-30
or graveman or nerolinux

see here fot k3b and audio cd's :
[http://www.ubuntuforums.org/showthread.php?t=22766](http://www.ubuntuforums.org/showthread.php?t=22766)

---

### Post by ntd on 2005-03-30
Have you installed mp3 support with Synaptic?

There is a how-to about it and other "Restrcited Formats"

If you can play mp3s fine, chances are you have already installed mp3 support, so just ignore this message :)

---

### Post by raum13 on 2005-03-31
[QUOTE=irad]Last night I was sitting trying to download some programs that will burn audio cd
(Mp3 --> CD), but I failed.
I also tried to download k3b, but it didn't recognize those mp3 files, and I don't know why,

Is there any program that can burn mp3 files into audio CD?[/QUOTE]

Hi 

the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb


with this you get a k3b which has 

/usr/share/apps/k3b/plugins/k3bmaddecoder.plugin
/usr/lib/kde3/libk3bmaddecoder.la
/usr/lib/kde3/libk3bmaddecoder.so

included. these are only included if during the compile the file mad.h is found. And as libmad0-dev is not required to compile k3b it is not downloaded during the "apt-get build-dep k3b" without the extra install you get a mp3 free k3b. (politcal reasons or just forgotten ?) 

cu r13

---

