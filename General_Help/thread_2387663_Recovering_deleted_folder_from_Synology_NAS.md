---
title: "Recovering deleted folder from Synology NAS"
date: 2018-03-22
forum: General Help
---

### Post by classicvag on 2018-03-22
Hi all

Hope to find someone here to help, other forums are not responding  :-(

Synology DS416 Play
3 x WD 3Tb + 1 Samsung 2Tb
SHR Raid with ext4 (at least i beleive it's ext4)

I managed to delete the default shared folder that contains all my photos...   [IMG]https://forum.synology.com/enu/images/smilies/icon_cry.gif[/IMG] 

I  have pulled out the drives and marked them with the slot they were in  (1-4). They are now connected to a desktop running Ubuntu 16.04 LTS via  USB to sATA adapters nad I hope it is possible to recover files using  "photorec" or something similar.
I have actually tried and photorec does recover files...thousands and thousands of them...

The  first attempt I tried was running Ubuntu from a USB and the logical  volume appeared in photorec. However, due to failure on the desktop  machine (PCI card) it had to be shut down and restarted and now I'm not  able to see the logical volume anymore, not with Ubuntu running from USB  or with Ubuntu installed.

One question I have is whether the order of the drives (sda, sdb, sdc and so on) has any impact?
The desktop I'm using has two internal drives (sda and sdb).

The  four NAS-drives are attached and showing up as /dev/sdc, /dev/sdc,  /dev/md126 and /dev/md127. The to latter ones are shown as RAID5 Arrays  on the "Disk" utility on Ubuntu.

I have tried various stuff, but are afraid of braking something beyond repair.

Can someone please help me out here?

---

### Post by classicvag on 2018-03-24
Bump

---

