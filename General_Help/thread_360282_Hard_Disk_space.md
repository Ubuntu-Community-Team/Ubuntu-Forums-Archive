---
title: "Hard Disk space"
date: 2007-02-13
forum: General Help
---

### Post by juantovarm on 2007-02-13
I just bought a 160 gb sata hd, took out my old 18 hda and reinstalled ubuntu via live cd.  Some questions arose when i checked the system monitor:

type ext3,  total 142.5, free 133.7, available 126.5

then i checked using ~$   sudo lshw -C disk, this came out: 

 *-disk
       description: SCSI Disk
       product: WDC WD1600JS-60M
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WCANM7348042
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 144GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 4400MB
          capabilities: extended partitioned partitioned:extended

Where has all the rest of the memory gone? Form 160 to 126.5? that is 33.5 gb,  almost twice the space of my old hd and almost  1/4 of my new disk.... :mad: ](*,) :-k

---

### Post by scrooge_74 on 2007-02-13
probably into SWAP and someting else

---

### Post by highneko on 2007-02-13
I don't understand that output. Maybe paste the out put of sudo fdisk -l && df -h?
It's worth noting that when they tell you it's 160GB, in most cases it's actually 156GB I think.

---

### Post by scrooge_74 on 2007-02-13
Yeah you are  right they usually round up the numbers

---

