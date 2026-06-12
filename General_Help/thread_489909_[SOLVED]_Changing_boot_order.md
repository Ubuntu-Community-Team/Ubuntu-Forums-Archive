---
title: "[SOLVED] Changing boot order"
date: 2007-07-01
forum: General Help
---

### Post by MadMac on 2007-07-01
I am dual booting between Ubuntu and windows XP, each on their own hard drive.  I have the windows drive as master and the Ubuntu one as slave.  I would like to change the jumpers to switch them and have Ubuntu as the master drive.

What I would like to know is if there is something special I should do before/after the change of boot order.

Thanks!

---

### Post by Scunizi on 2007-07-01
Why are you wanting to do this...? it's not neccessary and will mess up your boot process.  If you want to auto load Windows if you boot and walk away instead of Ubuntu that can be done without changing the drive order.

---

### Post by MadMac on 2007-07-01
> **Scunizi said:**
> Why are you wanting to do this...? it's not neccessary and will mess up your boot process.  If you want to auto load Windows if you boot and walk away instead of Ubuntu that can be done without changing the drive order.

I am having problems with grub (error 16 and 18 ) and this seems like the last thing I can test out.

Thanks!

---

### Post by Scunizi on 2007-07-01
I think you just need to reinstall Grub.. check out the guide.  It helped me a lot and was easy to follow.  It also mentions that it's a good idea to put grub on each HD (if the hd is marked bootable).  That way it won't matter which drive is chosen as master in the bios, it will still boot.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by MadMac on 2007-07-01
> **Scunizi said:**
> I think you just need to reinstall Grub.. check out the guide.  It helped me a lot and was easy to follow.  It also mentions that it's a good idea to put grub on each HD (if the hd is marked bootable).  That way it won't matter which drive is chosen as master in the bios, it will still boot.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Good info, thanks!

I did do another check with fdisk and found that a "storage" drive is showing as a boot drive:

=========
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156296384    78148161    7  HPFS/NTFS
=========

Maybe if I changed this?  Problem is that I don't know how to edit it so that it won't show as a boot drive.  It is formatted with ntfs, though.  Can you assist, please?

Thanks!

---

### Post by confused57 on 2007-07-01
> **MadMac said:**
> Good info, thanks!

I did do another check with fdisk and found that a "storage" drive is showing as a boot drive:

=========
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156296384    78148161    7  HPFS/NTFS
=========

Maybe if I changed this?  Problem is that I don't know how to edit it so that it won't show as a boot drive.  It is formatted with ntfs, though.  Can you assist, please?

Thanks!
Scunizi is not logged in at the moment, but I "may" be able to help you(since I wasn't in your other thread).

You can do this to install grub to your Ubuntu drive's mbr:
```
sudo grub
find /boot/grub/stage1
```
this should return something like "root (hd1,0)", you would then enter:
```
root (hd1,0)
setup (hd1)
quit
```
this should install grub to the mbr of your Ubuntu drive...try booting first to your Ubuntu drive, if you get a grub menu, highlight your Ubuntu entry, press "e" to edit, highlight your line with root, press "e" again, change root from (hd1,x) to (hd0,x)...x meaning leave this as is...press "enter", then "b" to boot.
This change is temporary, if it works, but it can be made permanent.

---

### Post by MadMac on 2007-07-02
Thanks, I'll give this a shot as soon as I finish downloading the "alternate" CD iso file.

Oh, I was also wondering about the * under the "Boot" where, from what I can tell, no * should be.  How can I change that?  Thanks!

Back tomorrow night, with all working right.  I hope. ;)

---

### Post by MadMac on 2007-07-03
> **confused57 said:**
> 

You can do this to install grub to your Ubuntu drive's mbr:
```
sudo grub
find /boot/grub/stage1
```
this should return something like "root (hd1,0)", you would then enter:
```
root (hd1,0)
setup (hd1)
quit
```
this should install grub to the mbr of your Ubuntu drive...try booting first to your Ubuntu drive, if you get a grub menu, highlight your Ubuntu entry, press "e" to edit, highlight your line with root, press "e" again, change root from (hd1,x) to (hd0,x)...x meaning leave this as is...press "enter", then "b" to boot.
This change is temporary, if it works, but it can be made permanent.

Sorry, nothing I did (I "played" with it) made a difference - I still get the 16 and 18 errors.

Maybe that * in the boot column in fdisk on the drive that is only for storage and is not bootable?  How can I change that, anyway?  I think that may have something to do with the boot order getting messed up and why I am getting these errors.

Any ideas/advice?

Thanks!

---

### Post by confused57 on 2007-07-03
> **MadMac said:**
> Sorry, nothing I did (I "played" with it) made a difference - I still get the 16 and 18 errors.

Maybe that * in the boot column in fdisk on the drive that is only for storage and is not bootable?  How can I change that, anyway?  I think that may have something to do with the boot order getting messed up and why I am getting these errors.

Any ideas/advice?

Thanks!
I don't think the * on your storage drive would affect your booting from grub, but I think you might be able to remove it by booting the live cd, go to System---Administration---Gnome Partition Editor, right-click the partition on this drive, select manage flags & I think you can remove the boot flag this way...read these instructions in another thread, I've always used the  Gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
the Ubuntu live cd should work just fine...


If you decide to reinstall Ubuntu, you may want to try manual partitioning and set up a small /boot partition(100-200 Mb) at the very beginning of the hard drive...this should eliminate the grub error 18, and hopefully the error 16?

---

### Post by MadMac on 2007-07-03
> **confused57 said:**
> I don't think the * on your storage drive would affect your booting from grub, but I think you might be able to remove it by booting the live cd, go to System---Administration---Gnome Partition Editor, right-click the partition on this drive, select manage flags & I think you can remove the boot flag this way...read these instructions in another thread, I've always used the  Gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
the Ubuntu live cd should work just fine...


If you decide to reinstall Ubuntu, you may want to try manual partitioning and set up a small /boot partition(100-200 Mb) at the very beginning of the hard drive...this should eliminate the grub error 18, and hopefully the error 16?

Did the partition editing with Gparted - no change.

Welllll...  I **really** don't want to reinstall Ubuntu, if I don't have to.  What with the restricted drivers and my monitor, it's almost like reinstalling windows.   ](*,)   I'll live with it, till it becomes **necessary** to reinstall, I guess, since it seems to be "one of those things".   :-k

Thanks for your help, I appreciate it!

---

### Post by MadMac on 2007-08-26
[Late post]

Well, I figured it out - it was a bad hard drive that was giving me errors.  Everything is running smooth as silk, now.

Thanks to all who helped!

---

