---
title: "grub error 23"
date: 2007-09-06
forum: General Help
---

### Post by qtrader on 2007-09-06
I have ubuntu 7.04 on a thinkpad R31 for a while.  It worked very well until a day ago when it failed to boot up and report this 

"error 23: error while parsing number, ubuntu".  

I can still boot up using the "recover mode", but not in the default mode.   This is very confusing to me now as I am newbie and my knowledge on grub is low, so I am desperate for any help from here :confused:



Below is part of /boot/grub/menu.lst: 

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c0c4a2c-5cb6-4d7c-8439-57e4daa0712f ro quiet nosplash vga= 0x314
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault



title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c0c4a2c-5cb6-4d7c-8439-57e4daa0712f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

---

### Post by merlinus on 2007-09-06
Press e at the grub menu to see what it says for root.  It should be (hd0,0).

-merlin

---

### Post by qtrader on 2007-09-06
Thank you Merline for help!  At reboot, the grub menu shows that it is "root  (hd0,0)". I only have one hard drive on this laptop and ubuntu is on the first partition. 
 



> **merlinus said:**
> Press e at the grub menu to see what it says for root.  It should be (hd0,0).

-merlin

---

### Post by lightstream on 2007-09-06
According to [this list]("http://www.ubuntu-forums.nl/kb.php?mode=article&k=34"):

23 : Error while parsing number
This error is returned if GRUB was expecting to read a number and encountered bad data.

How I would approach this would be to create a new grub menu option (by copy-pasting the 'recovery' one in menu.lst) and then change it bit by bit by adding from the non-working one until the error reoccurs.

---

### Post by merlinus on 2007-09-06
OK.  How about results of these commands:

```

sudo fdisk -l
blkid
cat /etc/fstab

```

-merlin

---

### Post by qtrader on 2007-09-07
Thanks for offering help from all of you!  To Merlin, the following is the output from my old R31:

> **merlinus said:**
> OK.  How about results of these commands:

```

sudo fdisk -l
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

blkid
/dev/sda1: UUID="7c0c4a2c-5cb6-4d7c-8439-57e4daa0712f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0d4f8c0e-f62c-42ee-b21e-23f9ff8ac5f7" TYPE="swap" 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c0c4a2c-5cb6-4d7c-8439-57e4daa0712f /               ext3    defaults,noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0d4f8c0e-f62c-42ee-b21e-23f9ff8ac5f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0





```

-merlin

---

### Post by confused57 on 2007-09-07
I don't know, but this might be your problem...change:
```
vga= 0x314
```
to
```
vga=0x314
```

The space after the = may be causing the problem?

---

### Post by qtrader on 2007-09-07
Thank you very much!  It can reboot normally now.  It must be the result of a recent ubutnu upgrade.  



> **confused57 said:**
> I don't know, but this might be your problem...change:
```
vga= 0x314
```
to
```
vga=0x314
```

The space after the = may be causing the problem?

---

### Post by confused57 on 2007-09-07
Glad it worked...I've had problems with spacing, uppercase vs lowercase, etc, requiring some "tweeting" to get things to function properly.

---

### Post by merlinus on 2007-09-07
Good eye, confused57!  Glad the problem is solved.

-merlin

---

### Post by confused57 on 2007-09-07
> **merlinus said:**
> Good eye, confused57!  Glad the problem is solved.

-merlin

I had to do a "double-take" before I caught the error...didn't catch it the first couple of times I read the original post.

---

### Post by wombat20 on 2007-09-26
I've recently got myself in a pickle by using grub-reboot. This is what I did to fix it.

1. Reboot into recovery mode (gives a root prompt).
2. Restored a backup I had made of menu.lst
3. Type the following at the command line.
```
grub
```
Then at the grub> prompt type (assuming 0 is the title you want to boot):
```
savedefault --default=0
reboot
```
Then back at the root prompt type:
```
shutdown -r now
```
That should get you back into ubuntu properly... still not sure why grub-reboot doesn't work for me.

---

