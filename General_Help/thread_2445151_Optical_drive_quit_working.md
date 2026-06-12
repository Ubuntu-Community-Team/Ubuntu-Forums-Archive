---
title: "Optical drive quit working"
date: 2020-06-09
forum: General Help
---

### Post by cscj01 on 2020-06-09
I am running Ubuntu 18.04.4 x64 with Flashback.  I have two DVD drives.  At some point between 18.04.3 and 18.4.4, one of my DVD drives quit working.  If I insert a CD (or DVD), it doesn't play.  It also doesn't show up in my places list.  I ran```
sudo lshw -C disk
```and got the following for my 2 optical drives> *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open

*-cdrom
       description: DVD-RAM writer
       product: BDDVDRW UH12NS30
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodiscI obviously see less information on the one than the other, i.e., no product or vendor information.
I also ran```
cat /proc/sys/dev/cdrom/info
```with the following results```
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:		sr1	sr0
drive speed:		1	40
drive # of slots:	1	1
Can close tray:		1	1
Can open tray:		1	1
Can lock tray:		1	1
Can change speed:	1	1
Can select disk:	0	0
Can read multisession:	1	1
Can read MCN:		1	1
Reports media changed:	1	1
Can play audio:		1	1
Can write CD-R:		1	1
Can write CD-RW:	1	1
Can read DVD:		1	1
Can write DVD-R:	1	1
Can write DVD-RAM:	1	1
Can read MRW:		1	1
Can write MRW:		1	1
Can write RAM:		1	1

```The drive speed of sr1 jumps out at me.  That can't be good, I assume.

The light comes on and flashes 4 or 5 times, then the drive goes silent.  I have read some post on the Internet that they have "lost" a dricve after an update.  Has anyone had this problem or have any ideas?

---

### Post by cscj01 on 2020-06-10
bump

---

### Post by kneutron on 2020-06-11
--I recommend you install the ' lsscsi ' package and issue ' lsscsi -s ', see if both show up.

--The only other thing I can think of is to try booting from your previous kernel version from grub.  If it shows back up and works normally, you probably caught a kernel bug.  If not, try another distro/livecd such as Knoppix and see if things work.  It may just be the drive died or you need to replace the SATA cable.

---

### Post by cscj01 on 2020-06-11
> **kneutron said:**
> --I recommend you install the ' lsscsi ' package and issue ' lsscsi -s ', see if both show up.

--The only other thing I can think of is to try booting from your previous kernel version from grub.  If it shows back up and works normally, you probably caught a kernel bug.  If not, try another distro/livecd such as Knoppix and see if things work.  It may just be the drive died or you need to replace the SATA cable.
I installed lssci with ```
sudo apt install lsscsi
```That installed fine.  I then issued ```
lsscsi -s
```and got the following```
[0:0:0:0]    disk    ATA      WDC WD2003FZEX-0 1A01  /dev/sda   2.00TB
[1:0:0:0]    disk    ATA      WDC WD1501FASS-0 1D05  /dev/sdb   1.50TB
[2:0:0:0]    cd/dvd  HL-DT-ST BD-RE  WH16NS40  1.03  /dev/sr0        -
[3:0:0:0]    disk    ATA      WDC WD5000AAKS-0 3B01  /dev/sdc    500GB
[4:0:0:0]    disk    ATA      WDC WD3003FZEX-0 1A01  /dev/sdd   3.00TB
[5:0:0:0]    cd/dvd  HL-DT-ST BDDVDRW UH12NS30 1.02  /dev/sr1        -
[7:0:0:0]    disk    ATA      WDC WD3000FYYZ-0 1K04  /dev/sde   3.00TB
[10:0:0:0]   disk    WD       Elements 107C    1042  /dev/sdf   3.00TB
[11:0:0:0]   disk    SanDisk  Ultra            1.00  /dev/sdg    123GB
[12:0:0:0]   disk    WD       Elements 25A3    1019  /dev/sdh   2.00TB
[13:0:0:0]   disk    WD       Elements 10A8    1042  /dev/sdi    500GB

```So they are both there.  I suppose I could have a laser that needs cleaning as well.  I will try to boot from the oldest kernel I have available to see if that helps.  Thanks for the suggestion.

---

### Post by cscj01 on 2020-06-12
Interesrting, I booted with kernel 5.3.51 and my drive works.  I am actually on 5.3.59 now.  I did not try 5.3.53, but I feel certain a kernel upgrade is what made my drive quit working.  So, my next question is, does anyone know how to rectify this short of filing a bug report?

---

### Post by ActionParsnip on 2020-06-12
What media players have you tried? VLC usually works OK and can access disks directly. I assume you are working with commercial video DVDs when you say "play"

---

### Post by cscj01 on 2020-06-12
With the 5.3.0-59 kernel, the system never recognizes that a disc has been inserted in the drive nor do any apps such as VLC.  With the 5.3.0-51 kernel, the system recognizes I have inserted a disc, and VLC works fine.

---

### Post by Yellow Pasque on 2020-06-12
```
configuration: status=open
```
Did you actually have the drive tray open when you ran the command? If not, then the system thinking the tray is open is probably the issue (or a symptom of it).
Can you run the lshw command again with 5.3.0-51?

---

### Post by cscj01 on 2020-06-13
> **Yellow Pasque said:**
> ```
configuration: status=open
```
Did you actually have the drive tray open when you ran the command? If not, then the system thinking the tray is open is probably the issue (or a symptom of it).
Can you run the lshw command again with 5.3.0-51?

The tray was not open when I ran the command.  In fact, I am back in 5.3.0-59, and I ran it again with the same result.  Thanks for that.  It was a good catch.  I will run it again under 5.3.0-51 tomorrow.  At the moment I am in the middle of a process that I have to finish before I reboot.

---

### Post by cscj01 on 2020-06-13
Okay here are the output values for the optical drives from  ```
sudo lshw -C disk
```under 5.3.0-53```
  *-cdrom
       description: DVD-RAM writer
       product: BD-RE  WH16NS40
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

  *-cdrom
       description: DVD-RAM writer
       product: BDDVDRW UH12NS30
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sr1
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


```So it seems that 5.3.0-59 **does** think the tray is open, even though it's not.  I also did ```
sudo lshw -C disk
```with a CD in the drive in question, and here is the result of the drive for that```
  *-cdrom
       description: DVD-RAM writer
       product: BD-RE  WH16NS40
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```Given that 5.3.0-59 thinks the tray is open when it's not, does anyone have any idea how I can get that reset under 5.3.0-59, or will I need to file a bug report?

---

### Post by Yellow Pasque on 2020-06-13
I'm not sure what to suggest except maybe playing with the eject command and looking at dmesg/journal.

---

