---
title: "[SOLVED] swap space not being used..."
date: 2007-06-09
forum: General Help
---

### Post by beorn! on 2007-06-09
Hey All,

I recently upgrade to 7.04, and since then I have noticed that my swap space is never being used, even when my ram is maxed out. Is there a way to initialize a swap space? Also, is there a  way to monitor activity on my swap?

when i run df i get...

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1            237383748   3507864 221817500   2% /
varrun                  517352       108    517244   1% /var/run
varlock                 517352         0    517352   0% /var/lock
procbususb              517352       140    517212   1% /proc/bus/usb
udev                    517352       140    517212   1% /dev
devshm                  517352         0    517352   0% /dev/shm
lrm                     517352     33788    483564   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1            488264768  15062784 473201984   4% /media/LACIE
/dev/sdf2              1862560   1849792     12768 100% /media/BEORNZ-IPOD


when i run mount i get...

/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077) [LACIE]
/dev/sdf2 on /media/BEORNZ-IPOD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077) [BEORNZ-IPOD]

I would run mkswap and add an extra swap space, then delete my old swap space and resize my hda1, but I didn't know if that was the best thing to do.... 

Any tips, tricks, etc, to optimize would be appreciated.

---

### Post by kerry_s on 2007-06-09
you want it using ram instead of swap, ram is faster. it just looks like it's maxed out because of cacheing apps for speed, it doesn't have to go to the hard drive to launch an app you have already used. it will use swap only when actually needed, otherwise it will just replace already cached apps.

---

### Post by beorn! on 2007-06-09
it's caching about 30% or so and 70%+ is in use by programs.... 

I guess the question still remains, how do I check to see if swap is available for use? And how can I better monitor it's history. Is there a swap log?

---

### Post by taurus on 2007-06-09
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by beorn! on 2007-06-09
Thank you very much. Very helpful commands. Looks like it's working. I ran quake 10x and finally got something to show up in my swap.....
-----------------------------------------------------------------------------
bemorder@prometheus:~$ fdisk -l
Password:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30024   241167748+  83  Linux
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    c  W95 FAT32 (LBA)
Note: sector size is 2048 (not 512)

Disk /dev/sdf: 2030 MB, 2030043136 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

--------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4f1f8785-387b-4031-b58a-26298455db6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7edd52d8-6a9e-43e0-980e-89f2e41687c2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

-----------------------------------------------------------------------------

             total       used       free     shared    buffers     cached
Mem:       1034708    1011804      22904          0      20132     702156
-/+ buffers/cache:     289516     745192
Swap:      3028212      33800    2994412
bemorder@prometheus:~$

---

### Post by taurus on 2007-06-09
```
total used free shared buffers cached
Mem: 1034708 1011804 22904 0 20132 702156
-/+ buffers/cache: 289516 745192
[COLOR="Blue"]Swap: 3028212 33800 2994412[/COLOR]
```
Well, your swap is being used.

---

