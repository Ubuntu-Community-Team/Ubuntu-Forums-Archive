---
title: "Booting winXp from GRUB, on SATA"
date: 2005-10-17
forum: General Help
---

### Post by indispus on 2005-10-17
Hello! I have Ubuntu Linux 5.10 installed on my ATA HDD, and WindowsXp on the SATA HDD.
I want to be able to boot WindowsXp from GRUB... so, I edit /boot/grub/menu.lst and add the fallowing lines:

```
title        WindowsXP
root        (**sd0**,0)
makeactive
chainloader    +1
```
But... when I try ti boot Xp, i get the fallowing error:```
Error 23: Error while parsing number
```

I tryied this too:
```
title        WindowsXP
root        (**hd1**,0)
makeactive
chainloader    +1
```
Still not working.... ```
Filesystem type unknown, partition type 0x7
```

**sudo cfdisk** returns:

[img]http://indispus.evonet.ro/temp/cfdisk.jpg[/img]


What should I do??? Help...

---

### Post by SilentCacophony on 2005-10-17
Hi. You used the correct notation in the second example. Grub uses (hdx,x) notation regardless of whether it's ATA or SATA, where the 'x,x' part is <drive_number,partition_number>, counting from 0.

You need to know the order of your drives, and the correct partition. Entering

**sudo fdisk -l**

in a terminal will show the order of your drives, and thier partitions. Once you identify the correct drive and partition, keep in mind that grub counts the first drive and partition as zero. For example, my setup:

```
Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         722     3293325   83  Linux
/dev/hda3             723        1338     4948020   83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)

```

If I wanted to boot from /dev/hda5, I'd use (hd0,4). Or /dev/hdb1 would be (hd1,0).

If you still are unsure, post back the output of **sudo fdisk -l**, and maybe someone can help.

---

### Post by indispus on 2005-10-17
I am still unsere. Here is my fdisk output:
```
Disk /dev/hdc: 4324 MB, 4324447744 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         499     4008186   83  Linux
/dev/hdc2             500         525      208845    5  Extended
/dev/hdc5             500         525      208813+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1589    12763611    7  HPFS/NTFS
/dev/sda2            1590       19457   143524710    f  W95 Ext'd (LBA)
/dev/sda5            1590       19457   143524678+   7  HPFS/NTFS

```

---

### Post by SilentCacophony on 2005-10-17
Hi, again. It does look as if (hd1,0) is the correct partition, since it has the boot flag:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1589    12763611    7  HPFS/NTFS
```

Looks to me like you may need to virtually 'map' the drives around in order to get Windows to deal with being on the second drive. Try this:

```
title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

There also may be some issue with your bios settings. Anyway, if you get an error with something about mounting with the above, you can try changing the 'root (hd1,0)' line to 'rootnoverify (hd1,0)'.

---

### Post by Xenus98 on 2005-10-17
Hi, as you look like to know GRUB quite goodly, may be you can help me as I am novice on ubuntu.

I managed to install ubuntu on an external USB hdd. My computer is a laptop.. that's why I did it. To save internal disk space. The GRUB boot loader has been installed on the internal HDD so. I worked hard to manage to make it found the USB drive (with mkinitramfs... long story).
I ended so with a dual boot.. .windows XP from internal drive, and ubuntu from external drive. BOTH are booting now OK !

I was very happy to make this work. Still, the day after, I didnt turn on my usb drive, and booted. Grub went immediatly off with an ERROR 21 (dont find drive...). For sure.

Any idea of what to do there ? I heard in some forum that I am suppose to manage to bring some file on the internal drive for GRUB to boot anyway... 
If you have a step by step solution/proposition.. please POST to save my life.
What a mobile computer if I cannot boot without my external HDD !!!!

Thanks a lot for taking care.

---

### Post by SilentCacophony on 2005-10-18
[QUOTE=Xenus98]Hi, as you look like to know GRUB quite goodly, may be you can help me as I am novice on ubuntu.

I managed to install ubuntu on an external USB hdd. My computer is a laptop.. that's why I did it. To save internal disk space. The GRUB boot loader has been installed on the internal HDD so. I worked hard to manage to make it found the USB drive (with mkinitramfs... long story).
I ended so with a dual boot.. .windows XP from internal drive, and ubuntu from external drive. BOTH are booting now OK !

I was very happy to make this work. Still, the day after, I didnt turn on my usb drive, and booted. Grub went immediatly off with an ERROR 21 (dont find drive...). For sure.[/QUOTE]

Hello. When you installed Ubuntu and installed GRUB to the MBR of the first drive, it wrote the /boot/grub/menu.lst file to the USB drive, which is where Ubuntu was installed. Therefore, the the first stage of grub, which is in the MBR, expects to find /boot/grub/menu.lst on the USB drive, and will fail if the drive is not there.

[QUOTE=Xenus98]Any idea of what to do there ? I heard in some forum that I am suppose to manage to bring some file on the internal drive for GRUB to boot anyway... 
If you have a step by step solution/proposition.. please POST to save my life.
What a mobile computer if I cannot boot without my external HDD !!!!

Thanks a lot for taking care.[/QUOTE]

There are probably several ways to fix that, but I do not know how to do any but one method. That involves making a boot floppy, and using the floppy to boot when the USB drive is detached. Of course, you must have a floppy drive for it to work, and the BIOS must support booting from floppy.

**EDIT** *- I just found another method for making a boot floppy [here]("http://ubuntuforums.org/showthread.php?t=76652"), looking at the first few comments. Not sure if it'd come out the same as my method, though.* **/EDIT**

If you want to try it, then connect the USB drive and boot Ubuntu. If you're running 'Breezy' (Ubuntu 5.10), then you should already have an /etc/fstab entry for your floppy drive. I will assume that is the case.

Insert a blank floppy disk, open a terminal, and enter the following commands:

```
sudo su
```

(enter password if necessary, and you'll have root access)

```
mkfs /dev/fd0
mount /media/floppy0
mkdir -p /media/floppy0/boot/grub
cp /boot/grub/stage1 /boot/grub/stage2 /boot/grub/menu.lst /media/floppy0/boot/grub
umount /media/floppy0
/sbin/grub --batch --device-map=/dev/null <<EOF
```

(here, the prompt will change to >)

```
device (fd0) /dev/fd0
root (fd0)
setup (fd0)
quit
EOF
```

(should see '...succeeded' near the end of the output)

```
exit
```

(goes back to user access)

This will make the floppy have the same boot menu as the one you currently have on the Ubuntu partition.

This method was derived from the official GRUB FAQ: 
[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q4](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q4)

Another way I have heard of, but do not know how to do, is to make a small partition on the first harddrive which will contain the /boot information, and install GRUB to the MBR using the /boot partition. Perhaps you might find more information on that from the above link. Good luck.

---

### Post by indispus on 2005-10-18
I tryied everything... still not working.


Filesystem type unknown, partition type 0x7

---

### Post by SilentCacophony on 2005-10-18
[QUOTE=indispus]I tryied everything... still not working.


Filesystem type unknown, partition type 0x7[/QUOTE]

Hi. You did try the '**rootnoverify (hd1,0)**' line, and it didn't work? AFAIK, that's often useful in clearing up the filesystem type error.

```
title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

If so, are you sure that the sda5 partition is not Windows XP? You have a ~13 GB and a ~147 GB partition there, and I can't tell which one it might be, except by guessing based upon the boot flag shown for sda1. Sda5 would need 'rootnoverify (hd1,4)', if you think it might be the correct partition.

**EDIT** [I]- a couple of links that may help, it editing by hand fails:

[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) <- older version of the above link, with more comments[/I]

---

### Post by indispus on 2005-10-18
```
title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

When i select this options in grub, I get a messaje like thins, on a black screen:
```
Booting 'WindowsXP'

rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```

...and it's freezing :(


With 'rootnoverify (hd1,4)', it still aint start. Windows is on sda1, the 13Gb partition.

[code]Error 18: Selected cylinder exeeds maximum spupported by BIOS[\code]

---

### Post by jonesy on 2005-10-18
what are the contents of your /boot/grub/device.map file?

---

### Post by indispus on 2005-10-19
Here is my /boot/grub/device.map:

```
(hd0)	/dev/hdc
```

---

### Post by indispus on 2005-10-19
In my /boot/grub/device.map, I add the fallowing line:```
(hd1)	/dev/sda
```

and, in my /boot/grub/menu.lst, I add the fallowing:```
title        WindowsXP
root        (hd1,0)
makeactive
chainloader    +1
```

but... stiil the same error:```
Filesystem type unknown, partition type 0x7
```

---

### Post by indispus on 2005-10-21
Other ideea?

---

### Post by indispus on 2005-10-23
???

---

### Post by Xenus98 on 2005-10-24
About the filesystem error 0x7 that you have, I remember last time I had it, meaned my drive partition filesystem was dead and had to reinstall windows NT... 

To me, it's look your windows is dead. Can you still boot on it ? I know some partition software will still tell you that they see the NTFS partition... but if I am right, you will never be able to boot on it or to access it via WinXP recovery console.

I hope I am wrong for you.

---

### Post by Seer on 2005-10-24
The problems cause is something that really annoys the crap out of me in both Ubuntu and Windows and just about every other distro.

If you have an IDE drive and a SATA drive in your PC, all the OS's just install their loader onto the IDE drive even if you have specified boot orders and all kinds in the BIOS that specifiy that the SATA is your boot device.

Seriously - a) give us the choice and/or b) Make it more intelligent.

---

### Post by jonesy on 2005-10-24
I googled for "Filesystem type unknown, partition type 0x7" and there are other people with the same problems but they seem to fix it by using 

  rootnoverify (hd1,0) 

instead of 

  root (hd1,0)

So you're final entry in /etc/grub/menu.lst should read:
[HTML]
title        WindowsXP
rootnoverify (hd1,0)
makeactive
chainloader    +1
[/HTML]

---

