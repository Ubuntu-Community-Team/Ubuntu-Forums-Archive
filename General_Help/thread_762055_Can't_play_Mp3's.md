---
title: "Can't play Mp3's"
date: 2008-04-21
forum: General Help
---

### Post by LasseNC on 2008-04-21
Hello guys! 

After I reinstalled Ubuntu, I am not able to play Mp3 files anymore. I installed the gstreamer things and ubuntu restricted extra, the last time I installed Ubuntu this wasn't a problem to get working, but I can't now. Any suggestions?

---

### Post by mc4man on 2008-04-21
do you have w32codecs ?

---

### Post by LasseNC on 2008-04-21
Yes, added the medibuntu repos. and installed them, didn't work.

When trying to play mp3 files in rhythmbox they just pause and when I change song then, they get a red sign.

---

### Post by jocko on 2008-04-21
> **mc4man said:**
> do you have w32codecs ?
That's not required for mp3 support. The ubuntu-restricted-extras package should give mp3 support.

---

### Post by mc4man on 2008-04-21
I've only used amarok - will ck. rhythmbox when I get home
If you have all the gstreamer plugins maybe Fluendo GStreamer MP3 plug-in

---

### Post by jocko on 2008-04-21
I think it is 'gstreamer0.10-plugins-ugly'.

---

### Post by LasseNC on 2008-04-21
Installed, still no sound. Will soon start pulling my hair out.

---

### Post by LasseNC on 2008-04-21
Also tried unstalling several plugins to not have any conflicts and then reinstall the recommended ones. To no avail

---

### Post by jocko on 2008-04-21
Do you have any sound at all? Is it only an mp3 problem?

---

### Post by LasseNC on 2008-04-21
I can play ogg

---

### Post by LasseNC on 2008-04-22
No one?

---

### Post by jocko on 2008-04-22
> **LasseNC said:**
> No one?

Have you tried another player? I tried rhythmbox yesterday and I have to say it's the worst player I have ever tried. It did play my mp3's, but the sound was almost completely drowned in white noise (and I really don't like music players that have to use a database engine to sort my music).

I use **audacious** for my mp3's and it works perfectly (It's a fork of beep-media-player, so it's pretty similar to old winamp 2.x and uses it's own codecs and plugins).
**Beep media player** and xmms are similar to audacious but older and no longer maintained.
**Totem** should play mp3's if you have the correct gstreamer-plugins package installed, and if you want a fancy database thingy similar to rhythmbox you could try **listen**, **BMPx** or **xmms2**.

---

### Post by trippinnik on 2008-04-23
amarok uses Xine.  I've had a problem in the past that was resolved by deleting the .xine directory in my home directory.  give that a try.

---

### Post by LasseNC on 2008-04-23
It worked after a reboot, imagine that I didn't think of that earlier.

---

