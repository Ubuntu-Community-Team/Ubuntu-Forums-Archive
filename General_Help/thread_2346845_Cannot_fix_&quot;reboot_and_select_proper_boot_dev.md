---
title: "Cannot fix &quot;reboot and select proper boot device&quot;"
date: 2016-12-19
forum: General Help
---

### Post by lucavassos on 2016-12-19
Hi everybody,

as you can get from the title, I have quite a common issue happening on my laptop (if matters it is Toshiba SATELLITE C50D-B-10U).
I read every article and thread about the "reboot and select proper boot device or insert boot media in selected boot device and press a key" error, but nothing worked.
Little story: Few days ago I tried to modify (unsuccessfully) my lvm partitions on Ubuntu. After going through many difficulties, I found a way to recover all my data and move them on a external hd.
Since I had nothing to save, I just loaded Ubuntu installer from a bootable usb, cancelled everything on my hdd and installed Ubuntu again.
The issue comes here: everything went fine, I rebooted my laptop and that is it, just had this annoying black screen with that error.
I tried with Boot Repair, everything went fine, then rebooted and nothing changed.
Tried to install Ubuntu again (with and without lvm partition mode), but nothing.
And of course I set the boot order with HDD in first position and my pc is running in UEFI mode.
Here you will find the info after running boot repair: [http://paste2.org/fK95P9ym](http://paste2.org/fK95P9ym)

Thank you a lot for helping, I really hope to work this out soon.


Luca

---

### Post by lucavassos on 2016-12-20
... No help? It is pretty important, I can't run my pc..

---

### Post by lucavassos on 2016-12-22
Hello again,

I finally worked it out. Now everything is working good, after several days of hell.
Pity that nobody could help, but I am new on this forum - luckily never had the need to be here - so I don't really know how it works.
:popcorn:

---

### Post by wildmanne39 on 2016-12-22
Since you found the solution please post it here so it will help other people with the same issue and use thread tools at the top of the page to mark the thread solved.
Thanks and glad you got it working.

---

### Post by lucavassos on 2016-12-24
Well I must say that I don't exactly know how I worked it out. Anyway I will post here what I have gone through so maybe it will be helpful to somebody. Here it is a very brief list of my steps:

Everything started when I tried unsuccessfully to reduce my ubuntu lvm partition to install another OS (Debian). After that, I was unable to boot properly my Ubuntu. So I just used the live cd to recover almost all my data - luckily I had few and only on my desktop.
After that I just erase my disk and installed completely Ubuntu. And from that moment on I had "reboot and select....." error on my screen every time I tried to boot.
I tried with boot repair - nothing.
I tried to work from grub shell with ls and commands to set boot - nothing.
I tried actually everything I could find on web. :D I tried to install again Ubuntu -lvm and not partitions- and nothing changed.
I tried also to install another OS - ubuntu studip - just to be sure it wasn't a problem of the OS I downloaded. - nothing.
So in the end I was so exhausted that I just decided to wipe my HDD so that my pc couldn't have any strange files of previous boots (I had windows 10 before) - also because I could see that every time I was installing a new OS I had different ls output in grub shell (even if I was installing exactly the same OS with same configuration).
After wiping, I tried install again ubuntu studio. Immediately it didn't work, so I decided to try again boot repair (just to be sure)...
and that's it. After boot repair, everything went fine. Now I am using even dual boot and everything is great.
So as you can see it was just a matter of trying more and more. 
....but it worked:D

---

