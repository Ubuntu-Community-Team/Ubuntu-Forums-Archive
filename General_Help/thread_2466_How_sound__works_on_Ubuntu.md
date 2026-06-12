---
title: "How sound  works on Ubuntu ?"
date: 2004-10-28
forum: General Help
---

### Post by jbarroso on 2004-10-28
Hi, I would like know how Ubuntu sound system is configured. I came from Debian. On Debian I can't play with rhythmbox and play togheter.

On Ubuntu, I can play with rhythmbox (Gstream), amarok (Xine), gnome notifications and play program (oss). It's wonderful, but I can't find how Ubuntu does it.

I think, it is alsa with oss emulation, but I can't configure my Debian like Ubuntu.

Do you know about it? Thanks you! Great work!

PD: Sorry for my english

---

### Post by Nis on 2004-10-28
Sounds like you don't have hardware mixing and your Debian system didn't use esd for software mixing.  Hardware mixing makes it possible to play multiple sounds at the same time.  Software mixing does the same thing albeit with some latency.  I know that Ubuntu uses esd for the system sounds and other stuff.

---

### Post by jbarroso on 2004-10-28
So .. How can I turn on software sound mixer on my debian, like on my ubuntu? 

My sounds etc related files are identical ... I'm lost ..

Thanks you!

---

### Post by Nis on 2004-10-28
Do you have esd installed an running?  Not sure how to do that on Debian since I came from Slackware.  There's always Google. :)

---

### Post by regeya on 2004-10-29
[QUOTE=jbarroso]So .. How can I turn on software sound mixer on my debian, like on my ubuntu? 

My sounds etc related files are identical ... I'm lost ..

Thanks you![/QUOTE]

Well, since you mention GStreamer, I can guess that you're using GNOME, so go to the Control Panels and select Sound.  Make sure "Enable sound server startup" is checked.  If it's not, check it.  Also, make sure that GStreamer is using the ESD sink.  If it's not, there's a GNOME control panel that can change this; sadly, I haven't found it under Ubuntu. What I did on this system was fire up the Configuration Editor and edit /system/gstreamer/0.8/default/audiosink.  Under Ubuntu, this is set to esddink by default.  I've got mine set to alsasink.   :smile:

---

