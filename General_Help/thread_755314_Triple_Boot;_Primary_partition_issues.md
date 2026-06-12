---
title: "Triple Boot; Primary partition issues"
date: 2008-04-14
forum: General Help
---

### Post by SlalomMan on 2008-04-14
I've got Ubuntu and Vista on my computer currently, and I want to try out another OS on there; be it XP or (illegally?) OSX...but I've ran into a bit of trouble.

I have 30GB of unpartitioned space on my hard drive, but I need to make another partition for the XP or OS X install. The problem is that I have four primary partitions already.

sda1 - 1.46GB partition - Toshiba's recovery partition (?); ntfs
sda2 - 186.43GB - Vista's space; ntfs
30 GB unallocated.
sda3 - 14.52GB - Ubuntu; ext3
sda4 - 486MB - Linux Swap; linux swap.

The four partitions are all primary; when I go to make a new partition for the new os I am told that I can only have four primary partitions. Also it says I should make an "extended" Partition so I can have more. I know linux fairly well but I don't know anything about partitions. Is there any way that I can make the linux swap not a primary partition?

Any help is appreciated.

---

### Post by logos34 on 2008-04-14
> **SlalomMan said:**
> 
sda1 - 1.46GB partition - Toshiba's recovery partition (?); ntfs
sda2 - 186.43GB - Vista's space; ntfs
30 GB unallocated.
sda3 - 14.52GB - Ubuntu; ext3
sda4 - 486MB - Linux Swap; linux swap.

 Also it says I should make an "extended" Partition so I can have more. I know linux fairly well but I don't know anything about partitions. Is there any way that I can make the linux swap not a primary partition?



You'll have to delete the swap (and grow root sda3 to take up the space).  Then create the extended out of the 30 gb space.  Put a new swap inside and edit fstab to match.

sudo swapoff -a
gksudo gparted

->delete sda4
->click unallocated space>new>extended partition (30 gb).
->click inside ext'd partition>create new linux-swap

gksudo gedit /etc/fstab

-> edit swap line (just take out 'UUID=' and use '/dev' format, i.e.

/dev/sda5 none swap sw 0 0

To extend root to take up the former swap you'll need to use gparted from the ubuntu live cd (the system cannot be mounted)

---

### Post by SlalomMan on 2008-04-14
Thanks so much for that information; Now I can throw on that extra OS; will that mess with my GRUB table? I notice in the tutorials (using windows) you have to set the new partition as active so it will boot; will I have to do that with mine? 

Maybe flagging it as boot, or adding it to the grub menu?

---

### Post by logos34 on 2008-04-14
Not sure about OSx but windows will definitely overwrite the grub bootloader with its own, and you'll have to [reinstall Grub]("http://ubuntuforums.org/showthread.php?t=224351") to get it back (easy).  Then add it to the bottom of /boot/grub/menu.lst so it appears on the grub startup screen.  And yes, you may have to toggle the boot flag on the windows partition (use gparted or cfdisk).  Although I have to say that the presence or absence of the boot flag on my own XP partition never prevented booting.

---

### Post by SlalomMan on 2008-04-14
Alright; When booting to OSX, it asks me where to install; it only shows my NTFS windows partition; when creating a partition under my extended one, I can only choose ext2, ext3, fat16, fat32, and reiserfs. Is there anyway I can use NTFS or Journaling there?

---

### Post by logos34 on 2008-04-15
> **SlalomMan said:**
>  Is there anyway I can use NTFS or Journaling there?

ext3 is basically ext2 w/journaling.  

As for creating a ntfs partition, you can always use gparted.

---

