---
title: "grub error 15"
date: 2007-04-30
forum: General Help
---

### Post by merlinus on 2007-04-30
After resizing two of my win2000 extended partitions, I am getting grub error 15, and cannot start my dual-boot system.

I am currently running from the ubuntu cd.

Is there any way to repair grub, or am I doomed to have to reinstall ubuntu from scratch and lose all of my customizations and preferences?

Many thanks....

-merlin

BTW, I can see all of the drives and their contents, both windows and ubuntu.

---

### Post by psusi on 2007-04-30
Mount your linux partition, for example:

sudo mount -t ext3 /mnt /dev/sda3

Then chroot into it:

sudo chroot /mnt

Then reinstall grub:

sudo grub-install /dev/sda

---

### Post by merlinus on 2007-04-30
I am able to view /boot/grub/menu.lst, but what needs to be changed so it will work again?

Here is the content:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ea0d79-f0a5-4381-a98d-08258758e696 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ea0d79-f0a5-4381-a98d-08258758e696 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

When I go into System Monitor/File Systems, after mounting all the drives, /dev/sda8 /media/disk is listed, so perhaps (hd0,6) needs to be changed to (hd0,8)?

Many thanks!

-merlin

---

### Post by confused57 on 2007-04-30
You might want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by merlinus on 2007-04-30
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2666    21414613+   7  HPFS/NTFS
/dev/sda2            2667        7297    37198507+   f  W95 Ext'd (LBA)
/dev/sda5            2667        3241     4618656    7  HPFS/NTFS
/dev/sda6            3242        3627     3100513+   7  HPFS/NTFS
/dev/sda7            3628        4909    10297633+  83  Linux
/dev/sda8            4910        6976    16603146   83  Linux
/dev/sda9            6977        7297     2578401   82  Linux swap / Solaris

---

### Post by confused57 on 2007-04-30
If your root partition is /dev/sda7, then (hd0,6) "should" be the correct root.  I'm just wondering if your UUID for your kernel line may have changed by repartitioning.
I'm not sure if this will work from the live cd, but you might try:
```
sudo vol_id -u /dev/sda7
```

it may need to be mounted first, I'm not sure:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda7 /media/ubuntu
```

then you should be able to find out with:
```
sudo vol_id -u /media/ubuntu
```

compare the UUID results with the UUID in your menu.lst kernel line.

---

### Post by merlinus on 2007-04-30
sudo vol_id -u /dev/sda7

gave no output, but....

sudo vol_id -u /dev/sda8
74ea0d79-f0a5-4381-a98d-08258758e696

So it looks like the UUID did not change.

What should I change in menu.lst, and how can I get to edit it?  So far it only opens in read-only mode.

Many thanks!  This is very upsetting....

-merlin

---

### Post by confused57 on 2007-04-30
Looks like your root partition  is now (hd0,7), if you get a grub boot menu when you boot your pc, highlight your Ubuntu entry, press "e", then change root to (hd0,7), then press "b" to boot.

If you're not getting a grub menu at boot, use the live cd to mount & change your menu.lst:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda8 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

this should enable you to change the root to (hd0,7)...quit & save.

---

### Post by Bigbluecat on 2007-04-30
There are fewer partitions than the numbers suggest. The root is hd(0,4).

---

### Post by confused57 on 2007-04-30
> **Bigbluecat said:**
> There are fewer partitions than the numbers suggest. The root is hd(0,4).

Good point, he may need to experiment & try (hd0,4), (hd0,5), etc, until he can find the actual root partition.

---

### Post by merlinus on 2007-04-30
The original root was (hd0,6).  changing it to (hd0,7) still gave me grub error 15.

I will try (hd0,4), but since it was originally (hd0,6), how can that be correct?

Also, although I can see /boot/grub/menu.lst and open it in read-only mode, I cannot access it from the terminal with

gksudo gedit /boot/grub/menu.lst

It gives an error message that /grub cannot be found.

Please forgive my ignorance, and many thanks....

-merlin

---

### Post by confused57 on 2007-04-30
Using the live cd, you're going to have to mount it each time you boot up:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda8 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

---

### Post by merlinus on 2007-04-30
I tried (hd0,4) 5, 6, 7, and 8, and still get the same grub error 15.

So it would seem that something else is going on.

Any ideas?

Or should I simply begin all over again with a fresh install.   :( :( :( 

Thanks....

-merlin

---

### Post by psusi on 2007-04-30
If you only resized existing partitions and did not add or remove any, then you do not need to change your menu.lst at all.   Please do as I said before and reinstall grub.  If you are getting the error before you even see the grub menu it is because grub itself can not be loaded, probably because you resized the partition it is on and thus, it is no longer in the same place.  It just needs reinstalled.

---

### Post by merlinus on 2007-04-30
As I prepared to reinstall from scratch, I did a search for NTFS-Config, as that would be a tool needed.

The solution in this thread fixed my problem --

[http://ubuntuforums.org/showthread.php?t=428415&highlight=ntfs-config](http://ubuntuforums.org/showthread.php?t=428415&highlight=ntfs-config)

I definitely was very fortunate....

-merlin

---

### Post by confused57 on 2007-04-30
Glad you were able to get it working...sorry I had to desert you, but something came up that I had to take care of.  I had considered maybe a filesystem check may be in order:

[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

Great job finding a solution yourself.

---

### Post by novus721 on 2007-04-30
I have had a similar problem, and I tried some of the things mentioned in this thread but I haven't had any luck

[http://ubuntuforums.org/showthread.php?t=429009](http://ubuntuforums.org/showthread.php?t=429009)

not trying to be a n00b but I am trying to do this in the middle of finals, and any help is greatly appreciated!

---

