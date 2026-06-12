---
title: "Server: Cannot load ubuntu! help!"
date: 2008-02-04
forum: General Help
---

### Post by mencargo on 2008-02-04
Hi there, I consider myself a intermediate user, I have used Ubuntu desktop before, now I have a project with Ubuntu Server.

First I installed Ubuntu Server 64bits 7.10, all went smooth, started configuring a web server, then I tried to go for Xen to have independent servers for local network, internet and isolate some special process.

But I found out there is no ubuntu-xen-server for 64 bit, so I tried to install it manually, got into big trouble configuring network, I had no access to internet, it was so frustrating I decided to go for 32bits.

So I installed Ubuntu Server 32bit 7.10, the installation went ok, but after reboot it freezes at some points, gives some error messages and takes forever to load, then I tried Ubuntu Server 8.04 32bit, and it does the same!!!

```
Starting up...
Loading, please wait...
```

This takes like 4-5 minutes, then:

```
kinit: trying to resume from /dev/disk/by-uuid/ .... lot's of numbers
kinit: No resume image, going normal boot
```

Another 2-3 minutes, then:

```
*Loading hardware drivers....
error receiving uevent message: No buffer space available
```

Another 5-8 minutes and it fails, if I leave it like half an hour it gets to the login prompt and it continues to load stuff up to "Running local boot scripts", it stops there and I can't login.
I have Intel DG33BU motherboard with core2quad Q6600 and 2x2Gb DDR2 800Mhz.
Help!!!
Either with a proper Xen setup for 64 bits or making 32bit work!

(I have 2 identical CPUs so I can try everything, please help)

---

### Post by pieisgood4589 on 2008-02-04
Burn another iso, or torrent, no FTP! Then check MD5.

---

### Post by mencargo on 2008-02-04
My personal computer, where I downloaded ubuntu server 7.10 64 and 32 bit versions, and 8.04 32bit, has only windows xp for now, do you know a simple way to make the checksum?

I found md5sha1checker sourceforge. (md5-checker-0.9.9.exe)
(that needs Java Runtime Enviroment)

My Hardy Ubuntu Server i386 ISO file (8.04) has the right MD5 checksum.
I didn't found a MD5 checksum for the ubuntu 7.10 server.

---

### Post by pointone on 2008-02-04
When you boot the CD, there should be an option to check the CD for defects at the boot prompt. Simply run this. You should also run Memtest86 on your system.

---

### Post by mencargo on 2008-02-04
I just checked my CD and it was ok.
I currently running Memtest86, 5 minutes, 1%... this may take a while.
Running out of ideas I decided to go for the Hardy Heron Ubuntu Server 64bits, that seems to include xen 3.2, currently burning it.

---

