---
title: "[SOLVED] Boot Problem"
date: 2007-06-20
forum: General Help
---

### Post by letubenaiah on 2007-06-20
I am new to Linux and had had a Ubuntu 7.04 and vista duel boot and decided to remove the vista partition and I'm thinking I did it wrong.  I just used gParted to remove the vista partition and reformat it into two ext3 partitions.  Now when I try to boot it still gives me the boot menu (I removed the vista part from the menu.lst file) but when I try to boot Linux it just gives me this error:

 Error 15: File not found

I am able to boot into Linux using the Super Grub Disk 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly' but when I reboot I get the same Error 15. 

What should I do to fix this problem and also to remove the boot menu completely.  Thanks for the help!

Benaiah

---

### Post by dreadlord_chris on 2007-06-20
> **letubenaiah said:**
> I am new to Linux and had had a Ubuntu 7.04 and vista duel boot and decided to remove the vista partition and I'm thinking I did it wrong.  I just used gParted to remove the vista partition and reformat it into two ext3 partitions.  Now when I try to boot it still gives me the boot menu (I removed the vista part from the menu.lst file) but when I try to boot Linux it just gives me this error:

 Error 15: File not found

I am able to boot into Linux using the Super Grub Disk 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly' but when I reboot I get the same Error 15. 

What should I do to fix this problem and also to remove the boot menu completely.  Thanks for the help!

Benaiah

Use your Super Grub Disk to reinstall GRUB
To remove the boot menu, find the following line in **/boot/grub/menu.lst**:
```

# hiddenmenu

```
and remove the **#** - *POOF* no more boot menu, if you do want to see it press the Escape key while booting.

---

### Post by letubenaiah on 2007-06-20
> **dreadlord_chris said:**
> Use your Super Grub Disk to reinstall GRUB


I've tried to reinstall GRUB using the SGD and it tells me that it has succeeded but I still have the same problem.

---

### Post by logos34 on 2007-06-20
Your root partition number has changed (I think that's it).

Boot from the live cd, load the desktop, open a terminal an type:
sudo fdisk -l

Has it changed?

---

### Post by merlinus on 2007-06-20
You might try this whilst you are booted into ubuntu:

```

sudo grub
find /boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute your results from find in the next two commands.

-merlin

---

### Post by letubenaiah on 2007-06-20
Thanks for the help guys!  But unfortunately it hasn't fixed the problem yet.

> **logos34 said:**
> Your root partition number has changed (I think that's it).

Boot from the live cd, load the desktop, open a terminal an type:
sudo fdisk -l

Has it changed?

Here is the output of sudo fdisk -l.  I don't know what partition number it was before but I think its a good guess that it has changed.
```

Disk /dev/sda: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot      Start       End      Blocks            Id      System

/dev/sda4                   1       19452   156248158+      f    W95 Ext'd (LBA)
/dev/sda5   *      10314       19074    70372701       83    Linux
/dev/sda6           19075       19452     3036253+        b   W95 FAT32
/dev/sda7                   1         1307    10498383        83   Linux
/dev/sda8             1308       10313    72340663+     83   Linux

```

> **merlinus said:**
> You might try this whilst you are booted into ubuntu:

```

sudo grub
find /boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

Substitute your results from find in the next two commands.

-merlin

Here is the final output of the setup command.  It didn't fix the problem.

```

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

Done.

```

---

### Post by logos34 on 2007-06-20
> Disk /dev/sda: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot      Start       End      Blocks            Id      System

/dev/sda4                   1       19452   156248158+      f    W95 Ext'd (LBA)
/dev/sda5   *      10314       19074    70372701       83    Linux
/dev/sda6           19075       19452     3036253+        b   W95 FAT32
/dev/sda7                   1         1307    10498383        83   Linux
/dev/sda8             1308       10313    72340663+     83   Linux

So this looks like one huge extended partition...and all you did was delete the first parition with vista and make two ext3, sda7-8, right?  sda5 (hd0,4) is clearly flagged bootable...so maybe there's a problem with the kernel line in menu.lst...if it's using the '/dev/sdx' method you'll need to change it, if UUID then i'm not sure if they stay the same when parition numbers change or not (I know the UUID's follow the partition when you clone them and move them around).

Pull up menu.lst  Anyone have a simpler way?

You have the mount root from the live cd first:

[B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda5 /mnt/ubuntu
sudo gedit /mnt/ubuntu/boot/grub/menu.lst[/B]

post it so we can check it out

---

### Post by logos34 on 2007-06-20
or try this (easier)

reboot to the grub menu, select the kernel and then hit 'e' for edit, then change root line to
**root (hd0,[COLOR="Blue"]4[/COLOR])**

hit enter

and the kernel line to read 

... **root=[COLOR="Blue"]/dev/sda5[/COLOR] ...**

enter and b to boot

---

### Post by letubenaiah on 2007-06-20
> **logos34 said:**
> or try this (easier)

reboot to the grub menu, select the kernel and then hit 'e' for edit, then change root line to
**root (hd0,[COLOR="Blue"]4[/COLOR])**

hit enter

and the kernel line to read 

... **root=[COLOR="Blue"]/dev/sda5[/COLOR] ...**

enter and b to boot

Thanks!  Its pretty much working now!  I only had to change the root line though to get it to boot.  Changing the kernel line gave me an error.  Now how do I save those settings so that I don't have to change it every time?

---

### Post by logos34 on 2007-06-20
> Thanks! Its pretty much working now! I only had to change the root line though to get it to boot. Changing the kernel line gave me an error. Now how do I save those settings so that I don't have to change it every time?

just edit menu.lst, changing the 'groot' line and each 'root' line for the entries in the automagic section to read 

**(hd0,4)**

---

### Post by letubenaiah on 2007-06-20
Great!  Its all working again.  Thanks for all the help!

---

### Post by logos34 on 2007-06-20
> **letubenaiah said:**
> Great!  Its all working again.  Thanks for all the help!

glad to know its running again!

Just one question: does your menu.lst and /etc/fstab use the UUID #'s or '/dev/sdax' format?

---

### Post by letubenaiah on 2007-06-21
> **logos34 said:**
> glad to know its running again!

Just one question: does your menu.lst and /etc/fstab use the UUID #'s or '/dev/sdax' format?

I think its UUID

here is the fstab:
```

# /etc/fstab: static file system information.
  2 #
  3 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  4 proc            /proc           proc    defaults        0       0
  5 # /dev/sda6
  6 UUID=d15e3da2-ac0b-4deb-b996-c2dd8cf353a2 /               ext3    defaults,e    rrors=remount-ro 0       1
  7 # /dev/sda7
  8 UUID=fdeac49b-08ec-4f64-b096-c119dcf99ef4 none            swap    sw                  0       0
  9 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
 10 /dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Thanks again!

---

