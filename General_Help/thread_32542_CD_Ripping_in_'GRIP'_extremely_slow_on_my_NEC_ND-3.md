---
title: "CD Ripping in 'GRIP' extremely slow on my NEC ND-3520A"
date: 2005-05-08
forum: General Help
---

### Post by GazaM on 2005-05-08
I have a NEC ND-3520A drive which is capable of 48x CD reading. One of the things I do most on my computer is rip music from CD to MP3 and this works extremely fast in Windows, but now that I have switched to Linux as my main Operating System I am trying to rip and encode my music onto the computer with the program GRIP. The problem is that it takes AGES to rip music from the CD, not even including encoding into MP3 a straight rip reaches a max speed of about 5.8x!! I've tried using the command line to encode mp3's from wav using LAME and it's extremely fast, so it's the rip from CD to wav that's taking GRIP so long. Can anybody suggest a fix for this?

---

### Post by astoltz on 2005-05-08
Sounds like you may need to enable DMA on your cdrom drive. Try (I'm assuming your cd drive is on /dev/hdc.  If it's not, replace that bit with the correct value for your system) ```
hdparm /dev/hdc
``` If it reports dma as "0" or off, do ```
sudo hdparm -d1 /dev/hdc
``` Then try grip again and see if that speeds things up.  You can make the change permanent by modifing /etc/hdparm.conf.  Good luck.

---

