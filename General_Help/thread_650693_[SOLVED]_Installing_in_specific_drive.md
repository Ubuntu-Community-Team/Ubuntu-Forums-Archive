---
title: "[SOLVED] Installing in specific drive"
date: 2007-12-26
forum: General Help
---

### Post by pakku on 2007-12-26
Hi,
My df command shows this
[FONT="Lucida Console"]/dev/sda6              3225252   2741788    319604  90% /
varrun                  257480       224    257256   1% /var/run
varlock                 257480         0    257480   0% /var/lock
procbususb              257480       108    257372   1% /proc/bus/usb
udev                    257480       108    257372   1% /dev
devshm                  257480         0    257480   0% /dev/shm
lrm                     257480     33788    223692  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              4096540   3803192    293348  93% /media/sda1
/dev/sda3              7645432   1145612   6111452  16% /media/sda3
/dev/sda5              4032092   3384648    442620  89% /media/sda5[/FONT]

As you can see I am rapidly running out of space on root.

I want to install Wine and then Irfanview and Picasa and want to do it on /dev/sda3 which has 6GB free.  But if I install Wine using Synaptic, it won't give me a choice on where to install it, right?  
So how do I actually force an installation on /dev/sda3?

And when I eventually install the Windows app Irfanview, will I have a choice where it goes?

I think Picasa does let me choose where to install (It is not available on Synaptic, anyway, so that question is moot!)

Thanks

---

### Post by Craigus on 2007-12-26
An alternative to all of this would be to use the gparted live cd to resize your root partition, stealing some space from the others.

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by pakku on 2007-12-29
> **Craigus said:**
> An alternative to all of this would be to use the gparted live cd to resize your root partition, stealing some space from the others.

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

Tx- I tried first the iso image from this above site but could not boot from that.  Ran into some errors with display settings (tried VESA/1024x768 but still didn't work.
So I used Ubuntu 7 install disk and got to gparted that way.

But it won't allow me to expand my root partition very much.  See attached bitmap below.

/dev/sda6 is the root and the most I can expand it is by the size of the swap partition which isn't much.  

Any ideas?

Tx

---

### Post by Craigus on 2007-12-29
Right click on /dev/sda3 and unmount it. Then you can shrink it, move the swap partition and grow /dev/sda6. But note that /dev/sda2 is an extended partition, so you will have to change the size of the whole extended partition before resizing the partitions within it. You will have to right click on swap and do swapoff to unmount the swap partition.

---

### Post by pakku on 2008-01-08
Thanks.
I could not resize **sda3 **even after unmounting it- it wouldn't let me shrink from the "left".  So I deleted it (I didn't have much data on it, just a few pics that I backed up)
Then I did the other stuff like moving the swap and growing **sda6 **and then recreated a new **sda3**.  See attached picture (gparted.jpg).

I must have obviously mucked up, 'cos when I reboot I get this screen (see picture onbootup.jpg) 
But, when I type in [FONT="Courier New"]shutdown -r now[/FONT] it brings me into the Ubuntu logon screen and I can work as usual.

Only problem is Nautilus shows **sda5 **and **sda3 **as having no files.  **sda3 **is of course empty since I recreated it but **sda5 **is unchanged, right?  And I can't "access" either of them.
If I boot into XP, I can see and access these drives and **sda5 **has all the files it had before my repartitioning.  I use that IFS control panel applet to be able to access ext3 drives from w/in Windows.

I tried safeboot into Ubuntu and running [FONT="Courier New"]fsck[/FONT], but it says disk is mounted (**sda6**) and wouldn't let me run it

Sorry to keep bothering you but any ideas?

---

### Post by Craigus on 2008-01-09
This thread probably has a solution:

[http://ubuntuforums.org/showthread.php?t=409180]("http://ubuntuforums.org/showthread.php?t=409180")

---

### Post by pakku on 2008-01-10
yeah, I saw that thread too after I posted my question.  It is not exactly my situation but it has got me started on looking at fstab entries with UUID's in them and so on.  Hopefully I will get there and then I can mark this thread closed!

---

### Post by Craigus on 2008-01-10
Good luck - I'm sure you'll get there.

> it wouldn't let me shrink from the "left".

Just for future reference, from memory what you do is shrink from the right and then move the whole partition to the right.

---

### Post by pakku on 2008-01-26
This is what I finally did- I dispensed with the UUID and used the /dev/nnnn notation in fstab and that fixed it.
New fstab
[FONT="Courier New"]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=45aaff09-95d5-408f-9702-7e6131f452c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=22C0EC0FC0EBE74F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
/dev/sda3 /media/sda3     ext3    defaults        0       2
# /dev/sda5
/dev/sda5 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=ee48ad5d-7be8-4313-a53f-17d30b8e303a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```[/FONT]

Old fstab
[FONT="Courier New"]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=45aaff09-95d5-408f-9702-7e6131f452c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=22C0EC0FC0EBE74F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=755635ed-d86f-4280-8ff1-bab4d1241eb4 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=44c7a295-52b1-4caf-a992-fb25071ea080 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=ee48ad5d-7be8-4313-a53f-17d30b8e303a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```[/FONT]

---

