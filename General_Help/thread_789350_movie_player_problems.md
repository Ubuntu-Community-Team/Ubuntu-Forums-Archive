---
title: "movie player problems"
date: 2008-05-10
forum: General Help
---

### Post by lkirlin on 2008-05-10
Hi, Im a newer user looking to run windows media and quicktime video files on my computer. Flash player runs fine for me but when it comes to running other proprietary formats video players such as totem and mplayer cannot run any files. Any help would be appreciated.

Im using gutsy and mainly having a problem with totem and mplayer. The problem with mplayer is that the video refuses to load, the screen is black with the play icon in the middle. When totem runs a video, it automatically exits itself from the screen.

---

### Post by fs3rp4 on 2008-05-10
> **lkirlin said:**
> Hi, Im a newer user looking to run windows media and quicktime video files on my computer. Flash player runs fine for me but when it comes to running other proprietary formats video players such as totem and mplayer cannot run any files. Any help would be appreciated.

Im using gutsy and mainly having a problem with totem and mplayer. The problem with mplayer is that the video refuses to load, the screen is black with the play icon in the middle. When totem runs a video, it automatically exits itself from the screen.

Hi, did you installed the w32codecs?

---

### Post by lkirlin on 2008-05-14
Ive just installed the w32 codecs however, the totem still refuses to play after the movie buffers. Mplayer boots up but then i get an error stating it couldnt open up the web site

---

### Post by lkirlin on 2008-05-14
Does anyone think if i upgrade to hardy my problem will be fixed?

---

### Post by fs3rp4 on 2008-05-14
> **lkirlin said:**
> Does anyone think if i upgrade to hardy my problem will be fixed?

Ok. Are you trying to watch these videos in a browser like Firefox?

If yes. try this:

sudo apt-get install ubuntu-restricted-extras




If the problem persist. try this

sudo apt-get remove totem-mozilla
sudo apt-get install mozilla-mplayer

---

### Post by wrgb2 on 2008-05-14
Have a look at [this forum post]("http://ubuntuforums.org/showthread.php?t=764221&highlight=extra+codecs+ubuntu") on how to enable viewing of most anything.  This was posted for Gutsy, but I followed it for Hardy and could view just about any multimedia type file.

---

### Post by lkirlin on 2008-05-26
I think the uninstalling the totem player and installing the mplayer package helped me out and solved my problem. thanks for helping out a linux noob like me :)

---

