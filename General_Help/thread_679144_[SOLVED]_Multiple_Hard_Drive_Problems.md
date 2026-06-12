---
title: "[SOLVED] Multiple Hard Drive Problems"
date: 2008-01-26
forum: General Help
---

### Post by slaguth on 2008-01-26
Hi, I am running Ubuntu Gutsy and XP on a machine with multiple hard drives. I am having problems because I recently cloned the drives, and I can't find a reliable way to determine which is which, or start up in the hard drive using the same process every time.

Anyway, I am having difficulty determining which hard drive I am running from at any given time, because System Monitor claims to run from /dev/sda2 no matter what hard drive I start up from, Hardware Information lists all my hard drives but doesn't give any indication which is currently running, and Disk Usage Analyser shows the same statistics for the two drives because despite being different sizes, the main ext3 partitions on each are both the same size.

Furthermore, I can't reliably choose to start up on the same drive using the bios, because even though it loads the grub from the correct drive (I modified menu.lst to be able to differentiate between them), grub doesn't always go out and start Ubuntu from the same drive it is running from.

For example, I have grub set to load splash on one drive but to skip the splash on the other. I started grub, went through verbose output (no splash), but when I looked at menu.lst it had "splash" listed on the kernel line. I restarted grub, chose the other drive in the bios, started up with splash, and when I checked menu.lst it didn't have "splash" listed.

But it isn't as simple as just grub loading from the opposite drive. It seems to be fairly random, in that selecting which drive to load in the bios (and thus which drive from which to load grub) has no reliable influence on which drive boots.

Any help or suggestions would be appreciated, as I really have no idea what is going on. Thanks in advance.

P.S. Here is some system information. I can provide more if that would be helpful.
Ubuntu Gutsy 7.10, fully updated
from ubuntu-7.10-desktop-amd64.iso
Kernel Linux 2.6.22-14-generic
AMD Athlon 64 X2 Dual Core 5600+
NVIDIA 8800 GTS, using the proprietary driver version 100.14.19
2.0 GB Ram

---

### Post by Tanker Bob on 2008-01-26
I had to edit /etc/fstab and /boot/grub/menu.lst manually to sort out my 4 drives. Two are RAIDed together, one has another Linux OS, and one has WinXP on it. The biggest issue is that GRUB assigned the wrong drives as default booters. Because the drive order was messed up, I had to guess at the correct drive designations. That worked, though.

One word of caution: don't use extended partitions on Linux drives. It seems to confuse the heck out of the drive order. Extendeds seem OK on Windows drives.

---

### Post by louieb on 2008-01-26
I take it you have an ext3 partition. You can use **e2label **to label the partitions differently. see the man pages. But an example to label **/dev/sda2** with the label **ubunturoot**
```
sudo e2label /dev/sda2 ubunturoot 
```And on a different note: 
> One word of caution: don't use extended partitions on Linux drives...Use extended and logical as you see fit. Linux doesn't care if a partition is primary or logical. (You can't have a logical partition without having an extended partition to hold it).
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by slaguth on 2008-01-26
> I had to edit /etc/fstab and /boot/grub/menu.lst manually to sort out my 4 drives.[...]

I am not exactly sure what your changes to fstab and menu.lst involved, so I am not entirely sure what to try. I did try to force grub to boot from the right drives by using UUIDs, which I believe are supposed to refer to the same drive even if the designation of the drive changes... but I got some strange results when looking for UUIDs using vol_id.

$ sudo vol_id -u /dev/sda2
77bdad5e-48ae-4b45-a82b-cc5920b36ac5
$ sudo vol_id -u /dev/sdc2
77bdad5e-48ae-4b45-a82b-cc5920b36ac5

sda2 and sdc2 are my main linux partitions... and it looks here like they have the same UUID.... But when I mount them they are clearly separate (I can for example find the different grub entries I mentioned in my last post). And sda2 and sdc2 always seem to refer to the same drives, even when grub is alternating between booting one drive or the other.

I really don't know what is going on with that...

And about partitions, I just let Ubuntu do its auto partition thing during install, so I really don't know what I have on my system... but what ever it is seems to be working fine, so I don't think that is the problem.

Again any help would be appreciated. Thanks.

---

### Post by logos34 on 2008-01-27
When you clone a partition, the UUID is copied with it.  

Why haven't you formatted the source drive you cloned from?  Unplug all your drives except that one, boot the live cd and use gparted to format the partition(s).  Then plug in the other hard disk(s).  [Reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351") if you have to.  As long as you're using either uuids or labels you shouldn't have anymore problems.

---

### Post by tact on 2008-01-29
You have discovered that when you clone disks you also clone the UUID and that sometimes has negative impacts.

To fix this you have to create new UUIDs for each partition on the cloned drive.  Then whenever 
both drives are plugged in to the same machine - all partitions will have unique UUIDs

Steps you must take for each and EVERY partition on the cloned drive:
1.  Generate a new UUID

At the terminal prompt type:
```
uuidgen
```
(a unique number you can use as a UUID will appear - copy to paste into next command)

```
sudo tune2fs /dev/sdb? -U paste_above_number_here
```
(replace sdb? with whatever your drive designation actually is - e.g. sdb2, hdb3, etc)

You can check the UUID associated with a partition with this command at a terminal:
```
vol_id /dev/sdb?
```

Repeat the above for each partition and now you will have a "clone" drive that at least has 
unique UUIDs for each partition and wont cause problems due to duplicated UUIDs caused by the cloning process.

note:  If you tried to change the UUID on your linux-swap partition above you got an error right?  To change the UUID for that linux-swap partition you are going to have to run a partition editor like gparted (sudo apt-get install gparted).  Delete the swap partition and recreate it.  This action generates and saves a new UUID.  Use vol_id to find what it is.

Now....if you changed the partition UUID's for any bootable partition,  that partition will no longer be able to boot because:
a.  the new UUIDS wont match your grub boot setup and
b.  the new UUIDs wont match the references in /etc/fstab

So....
EDIT MENU.LST and FSTAB
correct all the UUID's in both files.  (if you forgot it use the vol_id command to find out)

One more thing about bootable partitions and changed UUID's....  if you ever run "update-grub" the old UUIDs will come back and bite you.  trust me. 

And don't forget that some updates (like a new kernel) will have your system automatically run "update-grub" and so you dont escape saying you just wont do that.

So...
Now you have to actually boot from your new clone drive and since you edited /boot/grub/menu.lst to set the corerct UUID's it should boot.

 Once booted... delete  /boot/grub/ menu.lst and recreate it - this is the only way to get your new system to pick up the new UUIDs.  As mentioned above if you dont do this step... any time in the future an "update-grub" is done on this system the OLD UUIDs will turn up in your grub menu.lst and your system will not boot.

So the steps to backing up menu.list and deleting it in one step are:
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak

then:

sudo update-grub

Done.

---

