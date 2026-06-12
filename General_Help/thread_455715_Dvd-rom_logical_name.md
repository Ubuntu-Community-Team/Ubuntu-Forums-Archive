---
title: "Dvd-rom logical name"
date: 2007-05-26
forum: General Help
---

### Post by juantovarm on 2007-05-26
Does anyone know why my dvd-rom is named /dev/hdb. Shouldn't  it be named as /dev/scd0?
Like this, i do not get any mounted icons on my desktop or in "places". Is there a way to change the logical name to /dev/scd0? Is it because my only hard disk is sataII?

sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: TSSTcorpCD/DVDW SH-S182F
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: SB01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdb

---

