---
title: "TOTEM MOVIE PLAYER help"
date: 2005-06-04
forum: General Help
---

### Post by xbilly on 2005-06-04
Well I am beginning to get along with linux very well and I am getting better at certain things. One thing has been bugging me:

When I play a video, it only plays the audio and displays a blue screen thing. I have tried using other video players, but the same thing occurs. Any way of fixing this?

thank you, billy

---

### Post by flanker on 2005-06-05
Usually this happens when thes extra codecs havent been installed. Have you installed gstreamer-0.8-plugins + gstreamer-0.8-ffmpeg?

Add the universe and multiverse repositories;
=============================

sudo vi /etc/apt/sources.list

add the below lines;

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary multiverse


Install the codecs
=============

sudo apt-get install gstreamer-0.8-plugins
sudo apt-get install gstreamer-0.8-ffmpeg

---

### Post by xbilly on 2005-06-05
Yeah I did that... but still just audio and blue screen

---

### Post by NTolerance on 2005-06-05
[QUOTE=xbilly]Yeah I did that... but still just audio and blue screen[/QUOTE]

```
sudo apt-get install w32codecs
```

---

### Post by xbilly on 2005-06-05
no dice

---

### Post by az on 2005-06-05
[QUOTE=NTolerance]```
sudo apt-get install w32codecs
```[/QUOTE]


That would be for the xine backend to totem.  Totem can use the gstreamer libraries or the win32 libraries (by using xine).  On my machine, there are still some wmv files that are not playable.  I do not know if it is because by machines are too slow...

Do you have trouble with all media or just some files or file types?

---

### Post by xbilly on 2005-06-05
So far, all types as far as video/movies go.

---

### Post by pdk001 on 2005-06-09
[QUOTE=NTolerance]```
sudo apt-get install w32codecs
```[/QUOTE]
wmv file works fine for me
thanks so much for the tip

---

### Post by phen on 2005-06-14
try this command after download of gstreamer plugins etc:

kai@kai:~$ gst-register-0.8


it will register all downloaded codecs for gstreamer. I forgot it too :-(

---

### Post by joele on 2005-06-14
I use VLC, I found it more reliable with different AV files....

---

### Post by mike998 on 2005-06-14
I have a personal preference for Xine (sudo apt-get install xine-ui)

---

