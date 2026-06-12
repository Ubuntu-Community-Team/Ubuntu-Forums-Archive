---
title: "xmms trouble"
date: 2004-11-17
forum: General Help
---

### Post by keemo on 2004-11-17
Hi, 

this is a wierd problem. xmms has actually installed and I can run it without any problems, but when I press play it sort of goes through the song very quickly.

For example, a 2:30 minute MP3 file takes about 2 seconds for xmms to go through it.  everything looks as though its reading the file as the position seek bar moves, adn the visualisation box displays bars moving up and down, but the time ticks over in less that 2 seconds, and there is no sound output at all.

I tried installing mikmod (apt-get install mikmod) but to no avail...
has enyone had a similar problem?

My system - Athlon 1GHz, 256MB SDRAM, Gigabyte motherboard, nVidia GeForce4 128MB.

I searched on this forum, but I found nothing that is directly related to this problem.

Thanks in advance for you help

---

### Post by Marauder1 on 2004-11-17
You have a Nvidia base card !!!
Then you need to install libmikmod2 to
correct a bug.

from a console : sudo install libmikmod2

---

### Post by TravisNewman on 2004-11-17
the command is "sudo **apt-get** install libmikmod2"

---

### Post by Marauder1 on 2004-11-18
Sorry but panickedthumb is right
if forgot **apt-get**  :-#

---

### Post by keemo on 2004-11-18
thanks guys

I probably should have mentioned this in my original post, but I already did that, and the problem still exists. (i did do a search in here before i posted)

---

### Post by keemo on 2004-11-19
any other suggestions?

---

### Post by dook on 2004-11-19
[QUOTE=keemo]any other suggestions?[/QUOTE]

libmikmod2 is not for MP3 files, its for S3M/Mod files which were popular oh, about 8 years ago.  I found that I needed to install it because xmms crashed with an assertion failure without it, but it should not affect MP3 playback.

My XMMS also fails to play MP3 files, btw.

---

