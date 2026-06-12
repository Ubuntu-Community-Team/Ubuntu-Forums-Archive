---
title: "ffmpeg installation"
date: 2006-11-15
forum: General Help
---

### Post by w3bster on 2006-11-15
Could someone please help me to install these on a Ubuntu 6.10 LAMP:
FFmpeg ([http://ffmpeg.mplayerhq.hu](http://ffmpeg.mplayerhq.hu))
FFmpeg-PHP ([http://ffmpeg-php.sourceforge.net](http://ffmpeg-php.sourceforge.net))
Mplayer + Mencoder ([http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html))
flv2tool ([http://inlet-media.de/flvtool2](http://inlet-media.de/flvtool2))

Libogg + Libvorbis ([http://www.xiph.org/downloads](http://www.xiph.org/downloads))
LAME MP3 Encoder ([http://lame.sourceforge.net](http://lame.sourceforge.net))


I really searched all around the forums but... ](*,)  nothing. 
Thanks in advance.

---

### Post by mtn on 2006-11-15
have you tried using synaptic? system>administration>synaptic package manager

you might need to (once in synaptic) go to settings>repositories and check the "software restricted by copyright" option and maybe a couple of options, I can't remember exactly.  close repos window and click relod (top left) and seacrch for the packages.

this might also be helpful: [http://www.debian-unofficial.org/installation.html](http://www.debian-unofficial.org/installation.html)

and this: [http://www.getautomatix.com/](http://www.getautomatix.com/)

hope this helps

---

### Post by w3bster on 2006-11-16
I am useing the server version so ... no GUI :|

---

### Post by anaconda on 2006-11-16
Then you can just type:
```
sudo apt-get install ffmpeg
```
of course the success of this command depends in what repositories you have enabled in your /etc/apt/sources.list -file. 

If it didn't work edit your sources.list -file by:
sudo nano /etc/apt/sources.list
and remove the # from the beginning of those lines that have repositories addresses after the #
Save and type:
sudo apt-get update
sudo apt-get install ffmpeg

EDIT: just noticed that you wanted to install some other packages also.
you might need to add these 2 lines to the end of your sources.list
## PenguinLiberationFront (PLF) REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) edgy-plf free non-free

then just update your apt-get repositories and install all you want. You might need to use this: 
apt-cache search mencoder
to find the actual paggage names you want to install

---

