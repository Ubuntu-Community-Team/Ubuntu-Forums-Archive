---
title: "Need an SD card reader for ubuntu"
date: 2014-08-19
forum: General Help
---

### Post by yodals45 on 2014-08-19
Does anyone own a USB2.0 SD memory-card reader for Linux? 

I need to get one, but I can't find any advice on a brand or model.

I need one that will properly mount an SDHC card as an "mmcblk0". 
I tried 2 SDcard readers. The only one that worked mounted the card under the latest version of Ubuntu as "/dev/sdb1" and I couldn't seem to get write privileges.

I need some help here. x.X
It doesn't need to be USB, it just needs to work

---

### Post by dave131 on 2014-08-19
I bought the cheapest thing I could find at Micro Center - at $4 USB2 "55-in 1 Multi Card Reader".  It's always worked fine for me.  Right now I'm on a laptop I got free off our local Craigslist, and it doesn't have a hard disk (will be here in 2 days), so I'm actually booting and running Ubuntu via a SD card in that reader/writer.  Of course, it's only temporary until the drive gets here, but the point is the reader/writer works great.  As to where it mounts - that I don't know.  I would imagine you could always set up a link to mmcblk0 if you needed to.

---

### Post by yodals45 on 2014-08-19
I'm surprised so few people have card readers for Linux. All I need is a model name lol

---

### Post by coldraven on 2014-08-19
The card reader in my elderly laptop mounts an 8GB micro SDHC card as /media/1234-6789/ . This is in Ubuntu 12.04. 
I can read/write no problem. I do not understand your problem.

---

### Post by dave131 on 2014-08-19
> **yodals45 said:**
> I'm surprised so few people have card readers for Linux. All I need is a model name lolI think the point is you don't NEED a model name.  Any USB card reader/writer should work.  Whether it mounts at your specific mount point is not a matter of the reader/writer - that's in Ubuntu and how you set things up.  A fstab entry as an example can be set up to force mounting at a specific mount point.

Again - any USB card reader/writer should work.

As far as not getting write acces, you wouldn't access the device directly via /dev/sdbx.  Instead, that device (/dev/sdbx) needs to be mounted somewhere to access it.  This is where you can force it to mount at a specific mount point.  Right now I'd look under /media/<your userid> and see if it is mounted there.  Access the device via the mount point there.

EDIT:  It's probably worth asking as well what it is you are trying to do and why you need that specific mount point.

---

### Post by yodals45 on 2014-08-19
Hi dave131,
I'm trying to cross-compile an OS from a tutorial, to be loaded on the SDcard.
A lot of the commands are specific to an SD card.
SDCARD=mmcblk0
cat /sys/block/$SDCARD/device/name

When i try to run these commands on the SDcard I get errors like "not found" even when i enter the correct drive directory in the variable.
Some commands work, other spit out write errors.

I have no idea how to use fstab to properly configure mounting. I have searched in vain for instructions :/

---

### Post by yodals45 on 2014-08-19
nevermind, i got it! thanks for the instructions :P
learning experience.

---

