---
title: "looking for iso making software...... [Resolved]"
date: 2007-01-28
forum: General Help
---

### Post by stonerrob420 on 2007-01-28
Hello, I am looking for a program that makes iso images and can mount them in a virtual drive kinda like clone cd.......I have looked everywhere and have not been able to find one...Does any body have and suggestions on what program to use ?.....The version of ubuntu I use is 6.06 LTS...my computer is a gateway with a PGA 370 socket pentium III 566 mhz celeron with 512 sdram. the motherboard is a 4000655 intel. I'm using a cardinal 33.6 vf.c serial modem and a liteon dvd-rw. The harddrives are 2, 13 GB IBM deskstars . Any help would be much appreciated. :D

---

### Post by meng on 2007-01-28
Just use Nautilus CD/DVD burner, choose the files/folders as though you were going to burn to CD, then press Write to Disc, and choose to output to File Image instead of your burner. Instant ISO.

---

### Post by aysiu on 2007-01-28
K3B can make ISO images from CDs. And Qemu and VMWare Player can run the ISO.

---

### Post by taurus on 2007-01-28
If you want to mount an iso file, open a terminal and run

```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename.iso** /media/iso
```

---

### Post by MetalMusicAddict on 2007-01-28
Theres also [ISO Master]("http://littlesvr.ca/isomaster/"). [HERES]("http://www.getdeb.net/getdeb.php?file=isomaster_0.6-1getdeb1_i386.deb") a .deb.

---

### Post by stonerrob420 on 2007-01-30
thanx for everybodies help.....im very greatful

---

