---
title: "Flash in firefox 3 beta 2"
date: 2008-01-15
forum: General Help
---

### Post by andy_hubb on 2008-01-15
I can't get youtube videos to work on firefox 3, I think its because flash isn't installed - but i cant work out how to install it.

I've installed flash plugin non-free but it still isn't working...

---

### Post by benerivo on 2008-01-15
Download [flash]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") from the flash website, and extract the archive. Inside the the archive folder is a file called libflashplayer.so. Copy this in to /firefox/plugins (the same /firefox that has the executable firefox 3 in it). Then start firefox.

---

### Post by andy_hubb on 2008-01-15
I tried that - but I cant paste into the plugin folder? or is there some way I could do it in a terminal?

---

### Post by andy_hubb on 2008-01-16
anyone?

---

### Post by chewit on 2008-01-16
When is FF3 meant to be released fully?

---

### Post by NGSG on 2008-01-16
from Adobe,:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

download : install_flash_player_9_linux.tar.gz
and then simply 
tar zxvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
./flashplayer-installer
(this asks you where to put the .so file, give then the firefox library path)
hope this helps,

---

### Post by benerivo on 2008-01-16
> **andy_hubb said:**
> I tried that - but I cant paste into the plugin folder? or is there some way I could do it in a terminal?NGSG's guide will do ths, although i'm not sure why you can't paste in to the firefox/plugins folder. It sounds lke a permissions problem, but the beta 2 that you download can just be extracted and run i n your own user sapce so you shouldn't have any problems(?).

---

