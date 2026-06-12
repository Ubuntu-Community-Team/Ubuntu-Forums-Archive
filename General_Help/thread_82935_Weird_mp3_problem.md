---
title: "Weird mp3 problem"
date: 2005-10-27
forum: General Help
---

### Post by Youghurt on 2005-10-27
I've been searching how to make mp3s work on my Linux (breezy badger). However there's one slight problem: I can only play them while I'm logged in as root. 

I've tried downloading the pcakets and whatnot, but either one of these happens:
A) Packet not found/is missing but found a similar packet
B) installs packet

And after that, nothing happens. And when I'm trying XMMS it gives the following error: 
Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard.

In short WTF?

---

### Post by ipn1nj4 on 2005-10-27
This is a very common problem. Change your output plugin in XMMS.

Right click on XMMS and go to Options > Preferences and you'll see the tab there.

Change it from Alsa to OSS or esound

---

### Post by Youghurt on 2005-10-30
Thanks, changing it to Esound fixed the problem :p

---

