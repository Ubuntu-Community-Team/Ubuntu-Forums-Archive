---
title: "CD drives suddenly do not work, /dev/hdc not found"
date: 2007-12-01
forum: General Help
---

### Post by Damad on 2007-12-01
I'm on Ubuntu Gutsy Gibbon, for the record.

I have been doing much research, googling, forum reading, trying to figure out how to fix this problem, over the course of about 3 months, and having to spend the past few months without a cd drive in my computer, which I am positive should work fine. When I put a CD in either my CD-Rom drive or my CD-RW drive, they both sound like they are operating fine(all though while my CD-Rom drive used to work, the CD-RW drive has never worked). 

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8f5a4a87-aa24-4fe8-adfb-bbad24919e54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5dd651e2-44c3-414a-8b7c-a411349effe4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


When I try to open my CD-rom drive, it says "mount: special device /dev/hdc does not exist". And indeed, hdc is not found in the /dev/ folder. when i try to open my cd-rw drive, it says "There is probably no media in the drive", even though there is. I believe both drives work perfectly fine, except my CD-RW drive hasn't worked every since I installed Ubuntu.

Another thing I noticed, is that /dev/hdd is aimed at both drives...

dustin@axebox:~$ ls -l /dev/cdrw
lrwxrwxrwx 1 root root 3 2007-11-27 01:25 /dev/cdrw -> hdd
dustin@axebox:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2007-11-27 01:25 /dev/cdrom -> hdd

I also notice that my CD drive isn't even detected by ubuntu when i run the command lshw

*-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: 24X10X40 CD-RW
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet





I have been trying for months to fix this. I have found no solution any where. If someone could help, that would be god like.

---

### Post by geraldm on 2007-12-01
I have only one cdrw drive in my system, and when I ran as root "lshw" the drive was not detected either.  That may be a fault of that program.  The driver had no media in it when
I ran the command, and my fstab differs from yours in that I have "ro,user,noauto" in that one group.  The drive has been working, and it is never mounted when I create CDs.

To see what happened at boot time to the drives, try to run these commands against dmesg,
or /var/log/messages if dmesg is unavailable.

```

grep 'hdc' /var/log/dmesg
grep 'hdd' /var/log/dmesg

```

Gerald

---

### Post by Damad on 2007-12-02
So my cd drive started working randomly again. the CD-RW drive still does not work, though.

---

### Post by Damad on 2007-12-02
So this is what sudo lshw gives me now for my CD drives. I have a CD in each drive, but the CD-RW drive doesn't show up as having a CD in it. 

*-cdrom:0
                   description: IDE CD-ROM
                   product: IDE/ATAPI CD-ROM 44XS
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: T4W8
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: 24X10X40 CD-RW
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 2.02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw
                   configuration: status=nodisc

When I run the commands you told me to, I got the following message...

dustin@axebox:~$ grep 'hdd' /var/log/dmesg
[   57.545812]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:DMA, hdd:DMA
[    8.348000] hdd: 24X10X40 CD-RW, ATAPI CD/DVD-ROM drive
[    8.548000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
dustin@axebox:~$ grep 'hdc' /var/log/dmesg
[   57.545812]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:DMA, hdd:DMA
[    7.564000] hdc: IDE/ATAPI CD-ROM 44XS, ATAPI CD/DVD-ROM drive
[    8.528000] hdc: ATAPI 20X CD-ROM drive, 128kB Cache, UDMA(33)



Everything appears to work fine... the CD-RW shows up and everything. It cannot detect that there is a CD in the drive though and will not play or burn anything
Now that I look at it, it doesn't even try to read a CD when I put one in.... maybe the drive is dead? Is there a way to know that for sure?

---

### Post by geraldm on 2007-12-04
I would try putting a blank media in the CDRW drive and try to burn something, perhaps a CD-RW media, as an error should be correctable.  mount an iso image on the loop device to 
check the files, then try to write it if everything looks OK.  If the device does not burn it,
post the command used, as well as errors.  You may have to try writing as the root user if there are problems on the drive.

Gerald

---

### Post by broomie on 2007-12-13
I have exactly the same problem

2 x dvd drives one of them a RW. 

Ubuntu says there is no media in the drive, programs like kplayer, intermittently they recognise the music cd , list the tracks and then goes blank!

Mostly the drives although loaded mysteriously appear empty to Ubuntu.

drives work absolutely fine with Win XP!

I've had Mepis on thsi machien before and it worked fine too!


Paul

---

### Post by broomie on 2007-12-21
I have exactly same problem - works fine in Xpa nd previously with Mepis. Is intermittent too!

---

