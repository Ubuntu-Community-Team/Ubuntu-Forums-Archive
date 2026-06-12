---
title: "Playing Video files"
date: 2005-10-16
forum: General Help
---

### Post by unexpected on 2005-10-16
Currently, when I play .avi files, the video appears is "stilted." It appears to go frame by frame, and I receive no sound. Does anyone know what's going on and if i'm missing any particular packages?

I'm currently using Totem to play these .avi files...is there anything better?

---

### Post by ecobuntu on 2005-10-16
i use kaffeine.  you could try kaffeine or maybe mplayer.  do you have codecs for .avi files?

---

### Post by unexpected on 2005-10-16
what are the specific codec packs that i need?

I need codec packs for divX, xVid, .avi, etc. I have a huge media archive.

Can these packages be downloaded via synaptic or is there another repository i need to add?

---

### Post by munkymonkjr on 2005-10-16
you can just install VLC

```
sudo apt-get install vlc
``` it will play everything :)

also, yeah, just install all the codecs offered on the mplayerhq.hu site.

---

### Post by unexpected on 2005-10-17
apparently the mplayer website was down, I'll try it, but i'm wondering there's another place to get codecs from.

I'd really prefer a repository listing as i'm a wee bit uncomfortable building from source.

---

### Post by RyderDarkcrow on 2005-10-17
another option is to install EasyUbuntu, a script for Ubuntu newbies that, amongst a lot of other tweaks, installs a large number of common codecs.

see [this ]("http://ubuntuforums.org/showthread.php?t=64629")thread

---

### Post by afonic on 2005-10-17
The best you can do is read the Ubuntu guide:

[www.ubuntuguide.org](www.ubuntuguide.org)

Please note that the extra packages you can add following the instructions there are for Hoary, so be sure to change the text when adding sources.

---

### Post by aclaunch on 2005-10-17
Just a quick comment- you are not building the codecs from source (if you get them from the mplayer web site). They are mostly .dll files. Just download and copy to /usr/lib/w32codecs and they will be recognized.

Alan

---

