---
title: "[SOLVED] installing dmraid causes boot failure"
date: 2007-12-27
forum: General Help
---

### Post by BumbleBeeBinary on 2007-12-27
Hi I'm a noob to Ubuntu and I have a problem.

Here is the scenario...I have 3 hard drives all of which are SATA:

the first two (sda & sdb) are part of an isw raid set.
the raid array for these two disks have an ntfs file system with windows vista installed on it.

the third is sdc and not part of a raid array

I partitioned sdc into sdc1 sdc2 sdc3 & sdc4

sdc1 is my boot partition ext3 100 mb
sdc2 is my root partition ext3 75 GB
sdc3 is my swap partition swap 4096 MB
sdc4 is an ntfs partition used for storage

I installed Ubuntu on sdc and everything works great :)

The problem is as soon as I install dmraid (so that I can see my ntfs raid array on sda and sdb), Ubuntu compiles a new initrd.img which seems to make booting hang.  I took off the quiet switch from my boot string to see what happens but unfortunately, I can't see any errors because the system hangs after the screen goes black.

So I boot back into Ubuntu using the livecd and rename the newly compiled initrd.img to .old (initrd.img-2.6.22-14-generic.old).  I then took the backup initrd.img file (initrd.img-2.6.22-14-generic.bak) and renamed it to initrd.img-2.6.22-14-generic.  This allows Ubuntu to use the old initrd.img and everything once again boots up fine. I don't understand what exactly the initrd.img does but apparently it's not configured properly.

How can I diagnose what's going wrong during bootup? Any suggestions for a fix?

Below is my Grub menu:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=ba9a5232-b229-4f6e-9f09-b66622bab5cc ro splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=ba9a5232-b229-4f6e-9f09-b66622bab5cc ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

---

### Post by BumbleBeeBinary on 2007-12-27
no one can help with this?

---

### Post by fjgaude on 2007-12-27
The issue here is Ubuntu thinks it is to boot from drive a but when you connect the two raid drives the boot is really to be from drive c.

So when you get to the grub screen, type in "e", and change the root to (hd2,0) from (hd0,0). Once booted this way you will have to use the command line in Ubuntu to fix the grub.

It goes like this (wait for the grub prompt, it takes awhile sometimes):

```
sudo grub

grub> find /boot/grub/stage1

```
then:

>root (hd2,0)
>setup (hd2)
>quit

And if needed:

sudo grub-install /dev/sdc

I'm assuming that you will need to boot from the c drive. What you get from the find command tells you what you really need to do. hd2,0 is your drive sbc1.

Good luck and maybe a good study of the whole grub situation.

---

### Post by BumbleBeeBinary on 2007-12-27
grub actually works fine, that doesn't seem to be my problem...the kernel does start to load and it hangs after the screen goes black. If I had a problem with grub the kernel wouldn't even be loading.

---

### Post by BumbleBeeBinary on 2007-12-27
Could it be that after dmraid is installed, that the initrd has a problem with fstab? Which log file can I look for these boot errors? syslog and messeages?

---

### Post by fjgaude on 2007-12-27
If you are using Gnome, go to System/Administration/System Log. There you find many of the logs the system updates from boot-to-boot. Good luck.

I would still do the grub find to make sure I'm on the right stage1 page. <smile>

You know, sometime back, I tested dmraid using many different drive setups and never had any trouble re-booting. The system never seemed to change anything, certainly not fstab. Something to think about. Did you ever put any of the raid drives into a mode of being able to boot?

I had to manually mount my dm raid arrays until I placed an entry into the fstab file.

---

### Post by BumbleBeeBinary on 2007-12-27
> Did you ever put any of the raid drives into a mode of being able to boot?

Yes the raid is setup in the BIOS as a bootable raid stripe array. I actually use it to boot into windows when I'm not using Linux.

> The system never seemed to change anything, certainly not fstab.

This is what I'm afraid of...Here's why: When the system get's to grub, no kernel or ram disk has been loaded yet, therefore no raids can be discovered at this point.  So grub will still see my 3rd hard drive at hd0 not hd2 at this point.  However after the ram disk loads the kernel with the dmraid module, the kernel can now see 3 disks...my normal drive I have booted off of and now the raid array.  I think what might be happening is my fstab may be trying to mount my root partition from hd0 but by the time it get's to this particular step in the bootup process it's no longer hd0, it may be hd1 or hd2 because dmraid discovered new drives.

---

### Post by fjgaude on 2007-12-27
Let us see what you get from fdisk -l and show us the full fstab file. That might give some clue as to what is happening. Thanks.

---

### Post by BumbleBeeBinary on 2007-12-27
ok I tried the following:

> kevin@kevin-desktop:/$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd2) (hd2)1+17 p (hd2,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1
 (hd2,0)
grub> 


Is this correct?

---

### Post by BumbleBeeBinary on 2007-12-28
Alas...this didn't help...here is my fdisk:

kevin@kevin-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ddf328a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000015

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b687b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   83  Linux
/dev/sdc2              14        9574    76798732+  83  Linux
/dev/sdc3            9575       10096     4192965   82  Linux swap / Solaris
/dev/sdc4           10097       30401   163099912+   7  HPFS/NTFS

Disk /dev/sdf: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57b4fd21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       36483   293049666    7  HPFS/NTFS

---

### Post by BumbleBeeBinary on 2007-12-28
and my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=ba9a5232-b229-4f6e-9f09-b66622bab5cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc1
UUID=095a4ac0-ff31-4e27-a75d-515215404c28 /boot           ext3    defaults        0       2
# /dev/sdc4
UUID=7301B35E1937DB5D /storage        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc3
UUID=88cffaaf-7746-4449-865b-38a2454b3798 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by BumbleBeeBinary on 2007-12-28
found the problem!!!

sdc still had old raid metadata on it from a previous raid it used to be a part of.

I just ran the following command:

sudo dmraid -rE /dev/sdc

metadata erased and system now boots :)

---

### Post by fjgaude on 2007-12-28
Wonderful... I guess I was thinking of something like that when I asked about any of the drives ever being bootable, meaning having MBR and grub on them. Anyway, sometimes it takes time to sort out the issues... everyday we learn more.

Just think, you can now mount the NTFS raid while in Linux. <smile>

Happy New Year.

---

