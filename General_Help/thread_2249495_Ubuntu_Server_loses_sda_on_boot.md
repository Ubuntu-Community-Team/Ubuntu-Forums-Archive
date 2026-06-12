---
title: "Ubuntu Server loses sda on boot"
date: 2014-10-22
forum: General Help
---

### Post by landothedead2 on 2014-10-22
I'm having a real tough time with Ubuntu Server 14.04.1.
If the system boots properly then everything is fine and couldn't run better, but...
It successfully boots maybe every third time I power it on and these successes seem random (which make troubleshooting really difficult). From what I can tell the problem is that drives are being assigned different sdx on boot. For example running boot-repair gave me this:

===================
```
fdisk -l:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units  sectors of 1 *  = 512 bytes
Sector size (logical/physical: 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

```
However I know this is one of my storage drives due to the size and the fstab is supposed to mount this disk in sdb. Running fdisk on a successful boot gives me:

```

root@Landon-Server:/var/log# fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000616bd


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

```
My fstab is as follows:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/Landon--Server--vg-root /               ext4    errors=remount-ro 0$
# /boot was on /dev/sda1 during installation
UUID=c8712dc6-57d9-4cf6-8373-345aca40938a /boot           ext2    defaults     $
/dev/mapper/Landon--Server--vg-swap_1 none            swap    sw              0$
#Media1
UUID=96e3c717-c5da-4973-a3ab-2fadfa10e0af /media/Media ext3 defaults 0 0
#Media2
UUID=d4ec389f-341b-4a60-a910-eb32153c579f /media/MediaBack ext3 defaults 0 0
#Docs1
UUID=bfdbd282-84e9-47fb-8a85-7f21c407d9e5 /media/Docs ext3 defaults 0 0
#Docs2
UUID=b5547c29-db63-4973-a1d3-eb794676d119 /media/DocsBack ext3 defaults 0 0

```
I have quite a few disks, but this setup worked flawlessly using Ubuntu Desktop 14.04, so I can't figure out what the problem is. Any help would be appreciated.

---

### Post by tgalati4 on 2014-10-22
It's possible that your power supply can't spin up all of your disks fast enough.  Therefore they don't get enumerated.  Measure the 12VDC on your PSU.  If less than 12 volts, then you have a problem.

---

### Post by landothedead2 on 2014-10-23
Turns out the drive I had installed to was failing... which I should have picked up on. All is well now. Thanks.

---

