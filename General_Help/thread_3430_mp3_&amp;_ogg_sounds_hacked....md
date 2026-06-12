---
title: "mp3 &amp; ogg sounds hacked...???"
date: 2004-11-06
forum: General Help
---

### Post by sheimann on 2004-11-06
Hello @ all,

i hope someone has the same problem or a answer how to fix this problem.

I have successfully installed Ubuntu and followed the Multimedia HOWTO. 
All seems to work fine. I can play DVDs, CDs, rip CDs and Systemsound works fine too.

But if I try to play an mp3 or an ogg-file it sounds like it was hacked with a knife every half second (yes I have installed the gstreamer plugin :-) ).

I've tried varius settings, but nothing helps. 

Annybody knows how to fix this??

Hardware: Soundblaster LIVE (modul loaded without any error)
                 NVIDIA Geforce FX5950 Ultra (nvidia driver is installed and woked)
                 Adaptec AHAU160 (aic79xxx is loaded and works fine)

---

### Post by im_ka on 2004-11-06
what output are you using?

i've had the same prob with mplayer using alsa, and i've set oss for output, now it works fine.

run (assuming you're using rhythmbox)
```
gstreamer-properties
```

---

### Post by sheimann on 2004-11-06
[QUOTE=im_ka]what output are you using?

i've had the same prob with mplayer using alsa, and i've set oss for output, now it works fine.

run (assuming you're using rhythmbox)
```
gstreamer-properties
```[/QUOTE]
 Hello,

many thx for spending your time to help me. (and sorry for my bad english :-()

Currently I'm not able to test your hint. I'll give them a try at thursday. I'll let you know the reults.

mfg
sheimann

---

