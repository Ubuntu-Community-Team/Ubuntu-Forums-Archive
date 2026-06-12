---
title: "Firefox  problem in Ubuntu 14.04LTS?"
date: 2014-04-18
forum: General Help
---

### Post by frank18 on 2014-04-18
Hi guys;  Has anybody encountered bugs in the Ubuntu 14.04LTS in the  Mozila FireFox? i'm  struggling  with it at this time with the videoo streaming, it doesn't let me open  full screen on some sites, so much so i also downloaded Google Chrome and it runs much better! 
how to know what version of Firefox i am running? thanks

---

### Post by philinux on 2014-04-18
Moved to general help. 14.04 has been released.

---

### Post by su:bhatta on 2014-04-18
To know what firefox you are running :

Open Firefox, go to Help Menu and then select the last option ; About Firefox.
A small window should open with the version given.

---

### Post by Hreinsi on 2014-04-18
The FFmpeg plugin for GStreamer 0.10 is not available in the official Ubuntu 14.04 repositories (because FFMpeg is not available either - libav is used instead) and because of this, Firefox doesn't support the H.264 codec. 

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg

Maybe this will help
[http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html#more](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html#more)

---

