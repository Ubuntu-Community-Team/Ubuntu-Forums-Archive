---
title: "No video in Totem :("
date: 2005-05-13
forum: General Help
---

### Post by ntrsfrml on 2005-05-13
hey guys I installed ubuntu on my AMD64 box today.. updated all the media codecs

```

wget -c http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8
```

but still can't play .avi  with Totem.. only get sound :(

also tried re-installing the codec package.

please help.

---

### Post by Knome_fan on 2005-05-13
apt-get install totem-xine should fix that.

AFAIK gstreamer (at least in the version found on hoary) can't use the win32codecs, so in order to use the you need to run totem with the xine backend.  However, I have no idea if they work at all on AMD64, but as they seem to be available I figure they should.

Edit:
You should also install the gstreamer-ffmpeg package if you decide to stay with gstreamer.

---

### Post by ntrsfrml on 2005-05-13
[QUOTE=Knome_fan]apt-get install totem-xine should fix that.

AFAIK gstreamer (at least in the version found on hoary) can't use the win32codecs, so in order to use the you need to run totem with the xine backend.  However, I have no idea if they work at all on AMD64, but as they seem to be available I figure they should.

Edit:
You should also install the gstreamer-ffmpeg package if you decide to stay with gstreamer.[/QUOTE]

THank you so much!! THe XVID/AVI's are working now :)

---

