---
title: "/media drive not showing icon (other are)"
date: 2008-02-24
forum: General Help
---

### Post by pefdus on 2008-02-24
Hi 

I have a general question. 

What determines (and where is it configured) what mounted drives need to have volume icons to be shown ? And how does it all hang together ?
Some have said it is /media mounts which show icons, but I have found this is not entirely true.

My question relates to a bootable USB drive Ubuntu 7.10 installation.
This Ubuntu installation boots from a USB drive.
The drive is split into three partitions
part1 - fat32 
part2 - reiserfs (root /) [bootable]
part3 - swap

Primarily, this installation is booted from (on) a Laptop which has Windows XP installed.

Grub is installed on the USB drive and the Linux installation boots just fine.
(ie: root mounts from the 2nd part on the USB drive)
All mounting is done by UUID of the partitions.

**--- What I expect to occur ---**
I have a Windows XP partition on this laptop, which shows as an Icon on the desktop and is located at /media/winxp. The laptop drive is /dev/sda and /dev/sda1 is the ntfs WinXP partition.

When I boot, the drive icon for WinXP showing on the desktop.
This WinXP drive is listed in /etc/fstab as a mount.

If I umount (sudo umount /media/winxp) the drive, the icon on the desktop disappears.
If I mount, it comes back (naturally) .. good.

**-- What does not work ---**

The first partition /dev/sdb1 on the USB drive (the drive we boot from) is fat32.
It is in the /etc/fstab exactly the same as the WinXP partition.
It's mountpoint is at /media/LittleDisk

Two issues are arising
(a) it doesn't automount like the WinXP partition (in /etc/fstab) does.
(b) When I manually mount it, (sudo mount /media/LittleDisk) it mounts, but no icon appears.

Can someone please explain how Gnome determines which mounts should have icons.
Some have said it is mounts in /media. but in my case this can't exactly be the case.

Why would the WinXP be automounting, but the Fat32 on the USB disk not.
Any information would be appreciated.

Ramon

---

### Post by fragos on 2008-02-25
You could use the configuration editor but it's not all that user friendly.  I recommend you install the following and it provides a more strait forward GUI interface.

[http://getdeb.net/search.php?keywords=ubuntu+tweak](http://getdeb.net/search.php?keywords=ubuntu+tweak)

---

