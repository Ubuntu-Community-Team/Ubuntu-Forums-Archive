---
title: "w32 codecs installed but can't play mp3"
date: 2007-03-15
forum: General Help
---

### Post by Black^beret on 2007-03-15
Hi all i am new to ubuntu and have a problem listening to mp3 with rhythmbox   and also playing avi files  : i also installed w32codecs package but don't see any change
:confused: 
I have Edgy -- i heared that you have to edit your **extra repositories**   and **sources list**  but couldn't find support for **EDGY**  
someone can help me ?

---

### Post by Adam_GUI on 2007-03-15
> **Black^beret said:**
> Hi all i am new to ubuntu and have a problem listening to mp3 with rhythmbox   and also playing avi files  : i also installed w32codecs package but don't see any change
:confused: 
I have Edgy -- i heared that you have to edit your **extra repositories**   and **sources list**  but couldn't find support for **EDGY**  
someone can help me ?

You've chased the wrong rabbit, my friend.

You need libmad0 for MP3s.
And GStreamer-libmad0 to get them running in Rhythmbox.

---

### Post by aysiu on 2007-03-15
This should help:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by linuxwizard on 2007-03-15
Here is a link how to setup your repositories
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

This link shows what codecs you need to install everything under 6.10
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Hallvor on 2007-03-15
Or just install XMMS (looks just like winamp) for mp3 and VLC for video. They both have their own codecs, so you don`t have to install anything else.

---

### Post by Adam_GUI on 2007-03-15
> **Hallvor said:**
> Or just install XMMS (looks just like winamp) for mp3 and VLC for video. They both have their own codecs, so you don`t have to install anything else.

Except you don't get the indexing that Rhythmbox or AmaroK provide.  Indexing and searching your music gets addicting.  And sure beats searching through folders for the song you want to play.

---

