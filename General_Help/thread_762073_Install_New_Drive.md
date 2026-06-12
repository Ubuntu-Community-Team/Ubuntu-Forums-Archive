---
title: "Install New Drive"
date: 2008-04-21
forum: General Help
---

### Post by deamon_knight on 2008-04-21
I installed Ubuntu Hardy on a laptop with a vanilla CDROM drive. I installed a DVDRW drive and I'm having some problems. The Drive Reads CDs&DVDs normally, however when inserted, Totem tries to launch and reports "location not found", even though the Disk appears to mount properly. Also, when inserting a blank CD or DVD on another system running Gutsy, it mounts the disk as "blank writeable media". However this does not happen on my Hardy system, and it can't be selected as a destination by burning software.

I think I probably have to edit my Fstab, but I'm not sure where to go from here.

Here is my FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda11
UUID=562afe1b-6c19-4236-9070-7dc32738abd6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda13
UUID=3a4116ad-8421-4529-b73f-7832cfe28b80 none            swap    sw              0       0
 /dev/hdd        /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
<end>

And here is LSHW
           *-ide:1
                description: IDE Channel 0
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: TSSTcorp CDDVDW SN-S082H
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: SB00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm
                   configuration: status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/hdd
<end>

---

