---
title: "[SOLVED] unable to mount media (mp4) pls help"
date: 2008-03-06
forum: General Help
---

### Post by robertchahine on 2008-03-06
i have an mp4 (1GB) that i want to mount on ubuntu.the system see it as two drivers,but this is not the problem. when i open it tells "unable to mount media"?(but the system can read any USB flash memory or mp3 player).
and here my /etc/fstab :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fba97e20-cc21-440a-ae77-4ddaa8f08454 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=376ef518-913e-4046-8f62-3b61dd2855b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


what is the solution?

---

### Post by LuisGMarine on 2008-03-06
Plug in your MP4 player, and type in the following command, and then post the output:

```
sudo fdisk -l
```

---

### Post by robertchahine on 2008-03-09
it gives me :

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29032902

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1040 MB, 1040187392 bytes
32 heads, 62 sectors/track, 256 cylinders
Units = cylinders of 1984 * 2048 = 4063232 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table

---

### Post by LuisGMarine on 2008-03-09
[QUOTE=robertchahine;4481236]it gives me :

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29032902

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1040 MB, 1040187392 bytes
32 heads, 62 sectors/track, 256 cylinders
Units = cylinders of 1984 * 2048 = 4063232 bytes
Disk identifier: 0x00000000
[COLOR="Red"]Disk /dev/sdb doesn't contain a valid partition table[[/COLOR]/QUOTE]

For some reason its saying that your mp4 is not formated.  Try formatting it with gparted , then try again.  The partitions table might be screwed up, maybe hooking it up to a windows PC might also format it for you.

---

### Post by robertchahine on 2008-03-09
i installed the gparted.i launched after i plugged the mp4 player.don't know how to format it.
what to do know?

---

### Post by robertchahine on 2008-03-09
i don't know how, but after installing gparted, and scanning for devices.
the system now mount automaticly the mp4 player.
thank you LuisGMarine for the help

---

### Post by LuisGMarine on 2008-03-09
weird how things turn out to work!  :lolflag:

go ahead and mark this thread as [SOLVED] in the title.

Good luck !

---

### Post by fastwire on 2008-05-06
i just bought an mp3/mp4 player .. i have usb and cd (small ones) and on the cd i dont have drivers for xp i have only for windows 98 ... and my next ideea to upload music on my new mp4 :P was to try mount it in linux in usb devices ... anyway look what it gives me .. and please help me cause i wanna make it work :(
 
root@Knoppix:/ramdisk/home/knoppix# mount
/dev/root on / type ext2 (rw)
/ramdisk on /ramdisk type tmpfs (rw,size=826612k,mode=755)
/UNIONFS on /UNIONFS type aufs (rw,br:/ramdisk:/KNOPPIX)
/dev/hdd on /cdrom type iso9660 (ro)
/dev/cloop on /KNOPPIX type iso9660 (ro)
/proc/bus/usb on /proc/bus/usb type usbfs (rw,devmode=0666)
/dev/pts on /dev/pts type devpts (rw)
/dev/sda5 on /media/sda5 type fuseblk (ro,nosuid,nodev,noatime,allow_other,blksize=4096)
---------------------------------------------------------
root@Knoppix:/ramdisk/home/knoppix# cat /etc/fstab
/proc      /proc       proc   rw,nosuid,nodev,noexec 0 0
/sys       /sys        sysfs  rw,nosuid,nodev,noexec 0 0
/dev/shm   /dev/shm    tmpfs  rw,nosuid,nodev,noexec 0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /media/fd0  auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /media/cdrom  auto   user,noauto,exec,ro 0 0
/dev/hdd /media/hdd  auto   users,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/sda1 /media/sda1 ntfs noauto,users,exec,umask=000,uid=knoppix,gid=knoppix 0 0
# Added by KNOPPIX
/dev/sda5 /media/sda5 ntfs noauto,users,exec,umask=000,uid=knoppix,gid=knoppix 0 0
-----------------------------------------------------------
root@Knoppix:/ramdisk/home/knoppix# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        9729    62789632    7  HPFS/NTFS

please reply what i gotta do to upload music on my mp4 .. thanks in advance

---

### Post by fastwire on 2008-05-08
yo help me or not man .. i f .. tried gparted aint detectin nuthin .. on windows told ya i have cd only for win98 .. what dont u understood? say u dont know but dont u saw dat u "know" how 2 make it work but u dont answer or some other ...

---

### Post by robertchahine on 2008-05-09
> **fastwire said:**
> yo help me or not man .. i f .. tried gparted aint detectin nuthin .. on windows told ya i have cd only for win98 .. what dont u understood? say u dont know but dont u saw dat u "know" how 2 make it work but u dont answer or some other ...
what?

---

### Post by robertchahine on 2008-05-09
what is your poerating system?
i don't know how, but gparted solved my issue.
and now i'm on hardy, and no need for gparted, because the system automatically mount the mp4 player.

but you should give this a look it might help 

[http://ubuntuforums.org/showthread.php?p=4679636](http://ubuntuforums.org/showthread.php?p=4679636)

---

