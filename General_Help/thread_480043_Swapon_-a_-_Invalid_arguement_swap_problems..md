---
title: "Swapon -a - Invalid arguement?? swap problems."
date: 2007-06-21
forum: General Help
---

### Post by wastedfluid on 2007-06-21
Hi  guys.

Long story, will try to keep short.  My swap file does NOT automount; however, /sbin/mkswap will activate it.  Sorry for such a long post, but I tried to include EVERYTHING you could possibly need!  The only way I have found to activate/mount my swap is "/sbin/mkswap /dev/hda5" - and it will not automount on boot!  thanks guys!

(how I can activate swap manually.)
> 
wastedfluid@wastedfluid:~$ sudo mkswap /dev/hda5
Password:
Setting up swapspace version 1, size = 1965805 kB
no label, UUID=7e5adb69-b5a1-42d6-9ab9-7aef051c6870
wastedfluid@wastedfluid:~$ free
             total       used       free     shared    buffers     cached
Mem:        904644     593064     311580          0      74828     293540
-/+ buffers/cache:     224696     679948
Swap:            0          0          0
wastedfluid@wastedfluid:~$ sudo swapon -a
wastedfluid@wastedfluid:~$ free
             total       used       free     shared    buffers     cached
Mem:        904644     594108     310536          0      74852     293792
-/+ buffers/cache:     225464     679180
Swap:      1919728          0    1919728
wastedfluid@wastedfluid:~$



Here are the goodies(This is WITHOUT typing mkswap /dev/hda5)

> 
wastedfluid@wastedfluid:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument


fstab:
> 
astedfluid@wastedfluid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


ls -al:
> 
wastedfluid@wastedfluid:~$ ls -al /dev/hda5
brw-rw---- 1 root disk 3, 5 2007-06-20 19:49 /dev/hda5



df:
> 
wastedfluid@wastedfluid:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              55G   17G   36G  33% /
varrun                442M   96K  442M   1% /var/run
varlock               442M  4.0K  442M   1% /var/lock
udev                  442M  104K  442M   1% /dev
devshm                442M     0  442M   0% /dev/shm
lrm                   442M   19M  424M   5% /lib/modules/2.6.15-28-386/volatile
wastedfluid@wastedfluid:~$


fdisk:
> 
wastedfluid@wastedfluid:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   12  Compaq diagnostics
/dev/hda2   *         638        4462    30724312+   c  W95 FAT32 (LBA)
/dev/hda3            4463       11922    59922450   83  Linux
/dev/hda4           11923       12161     1919767+   5  Extended
/dev/hda5           11923       12161     1919736   82  Linux swap / Solaris
wastedfluid@wastedfluid:~$



sfdisk:
> 
wastedfluid@wastedfluid:~$ sudo sfdisk -l /dev/hda  Disk /dev/hda: 12161 cylinders, 255 heads, 63 sectors/track Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1          0+    636     637-   5116671   12  Compaq diagnostics
/dev/hda2   *    637    4461    3825   30724312+   c  W95 FAT32 (LBA)
/dev/hda3       4462   11921    7460   59922450   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda4      11922   12160     239    1919767+   5  Extended
/dev/hda5      11922+  12160     239-   1919736   82  Linux swap / Solaris
wastedfluid@wastedfluid:~$




and, finally, free shows:
> 
wastedfluid@wastedfluid:~$ free              total       used       free     shared    buffers     cached Mem:        904644     534444     370200          0      72164     252660 -/+ buffers/cache:     209620     695024
Swap:            0          0          0
wastedfluid@wastedfluid:~$




---

### Post by wastedfluid on 2007-06-21
bump..

anyone?

---

### Post by odiseo77 on 2007-06-21
Hi, I'm having the same problem after installing Debian Etch on my Ubuntu PC and I think it's because of the new way ubuntu's /etc/fstab handles the partitions; now I think we must add the UUID of the partition on /etc/fstab instead of the device name. Your post has given me ideas, though... I see that when you run 'sudo mkswap /dev/hda5' it shows you the swap partition's UUID; try replacing the swap partition UUID on your /etc/fstab with the one you get when you run 'sudo mkswap /dev/hda5'. I'm gonna try it myself in a few minutes and let you know how it goes (had not tried before because didn't know mkswap gave you the partition's UUID).

Greetings.

EDIT: Yep, it works!! All you have to do is to replace the UUID of the swap partition on your /etc/fstab, reboot, et voilà, you're done ;)

---

### Post by wastedfluid on 2007-06-21
> **odiseo77 said:**
> Hi, I'm having the same problem after installing Debian Etch on my Ubuntu PC and I think it's because of the new way ubuntu's /etc/fstab handles the partitions; now I think we must add the UUID of the partition on /etc/fstab instead of the device name. Your post has given me ideas, though... I see that when you run 'sudo mkswap /dev/hda5' it shows you the swap partition's UUID; try replacing the swap partition UUID on your /etc/fstab with the one you get when you run 'sudo mkswap /dev/hda5'. I'm gonna try it myself in a few minutes and let you know how it goes (had not tried before because didn't know mkswap gave you the partition's UUID).

Greetings.

EDIT: Yep, it works!! All you have to do is to replace the UUID of the swap partition on your /etc/fstab, reboot, et voilà, you're done ;)

Show me your fstab???  I'll try this, I think I know what you're talking aobut.. lettme check!

*EDIT*

Nope.  No luck.  Paste me your FSTAB w/ your UUID's.. I'll use it to make a new fstab.. and if I mess it up, a simple replacement of a backup will work.

---

### Post by odiseo77 on 2007-06-21
My fstab won't work for you because each partition has an unique UUID, so take a look at [this post]("http://ubuntuforums.org/showpost.php?p=2880231&postcount=7"); basically, what you have to do is to execute: 

```
sudo vol_id -u /dev/hda5
```

This will give you the UUID of your swap partition. After this open /etc/fstab:

```
gksu gedit /etc/fstab
```

You'll find an entry like this one:

```
# /dev/hda5
UUID=56675760-4a80-49b8-b6db-f69d11aef389 none            swap    sw
```

Replace the number after 'UUID=' which the output of the first command I posted. After this, save the file, reboot, and you're done.

Greetings.

EDIT: Wait a second, are you still using dapper?? if this is the case, the proceeding will be totally different, I think, so we'll need your ***sudo fdisk -l*** output.

---

### Post by KongKNoob on 2007-06-26
I'm having similar problems, and hope you can help me as well. My swap doesn't automount at startup, but I can mount it using swapon. I did a fstab -l an it returned:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9561    76798701   83  Linux
/dev/hdb2            9562       27919   147460635   83  Linux
/dev/hdb3           27920       30515    20852370   82  Linux swap / Solaris

```
(Yes, I know my swap is monstrously large...)

But fstab looks like this:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/hdb1 :
UUID=50827c02-e90c-4530-82fc-fd660a9c0b87 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/mapper/hdb2 :
UUID=a90cb87c-3cae-4b25-bfdd-15d16c9f369d /home ext3 defaults 0 2
# Entry for /dev/mapper/hda1 :
UUID=8EDCB856DCB839F3 /media/hda1 ntfs-3g defaults,locale=nb_NO.UTF-8 0 1
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=nb_NO.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=2a927062-7084-43bf-9156-f711ed7eec50 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Should I just fill in the blanks? and with what?

thanks :D

---

### Post by odiseo77 on 2007-06-26
Try this:

```
sudo vol_id -u /dev/hdb3
```

This command will give you the UUID of your swap partition. Then edit your /etc/fstab file and replace the UUID for your swap partition with the output of the previous command, reboot and it should work... There's something that puzzles me though, the swap entry on your /etc/fstab says "# Entry for /dev/ !! UNKNOW DEVICE !! :" so there might be anything wrong with that...

---

### Post by KongKNoob on 2007-06-27
Edited my fstab like you suggested, and it worked like a charm. Thanks! :KS

---

