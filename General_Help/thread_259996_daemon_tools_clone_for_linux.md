---
title: "daemon tools clone for linux?"
date: 2006-09-18
forum: General Help
---

### Post by pppetter on 2006-09-18
Hi everyone!

Just wondering, does anyone know about a daemon tools like program for ubuntu/linux?

From Deamon tools homepage:
"DAEMON Tools is a virtual cd/dvd-rom emulator. It is able to emulate nearly all known copy protections on the market today."

---

### Post by franestepona on 2006-09-18
use mount from the command line.

Do:

sudo mkdir /media/img
sudo mount -o loop [file.img or iso, just make sure there is no spaces in the filename]  /media/img

---

### Post by lamego on 2006-09-18
If you need to mount .iso files thats a native function on Linux.

Read how to do it at:
[http://aplawrence.com/Unixart/mount_iso_image.html](http://aplawrence.com/Unixart/mount_iso_image.html)

---

### Post by NewbieLearnLinux on 2006-09-18
> If you need to mount .iso files thats a native function on Linux.

lol !

---

### Post by pppetter on 2006-09-18
how cool isn't that? a native function!

thx

---

### Post by hw-tph on 2006-09-20
For non-standard images like Goldenhawk type CD images (.cue/.bin file combination), mds, ccd and Nero (.nrg) images loopback mounting will not work. You can use [cdemu](http://cdemu.sourceforge.net/) to mount these.


Håkan

---

