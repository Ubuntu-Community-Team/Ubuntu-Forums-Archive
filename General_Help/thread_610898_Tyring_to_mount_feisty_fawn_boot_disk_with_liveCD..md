---
title: "Tyring to mount feisty fawn boot disk with liveCD.. HELP!"
date: 2007-11-12
forum: General Help
---

### Post by malibu on 2007-11-12
Hi there.  I run Ubuntu (Feisty Fawn Server) on a VMWare box and the size of my virtual disk has gotten out of control.  So far as I can tell, the only way to 'shrink' the disk whilst avoiding having to build VMWare Tools on Ubuntu is by cloning the disk to a new virtual disk within Ubuntu and swapping them.  I tried cloning with g4u but unfortunately it copies the useless data along with the good, so you end up with an even bigger virtual disk.

So I am attempting my cloning in a new dummy VM with the Gutsy Gibbon Live CD, but I can't figure out how to mount the disk.  So I attached my original disk and a new disk to a new VM and booted with the CD.  Then I did the following:

# cd /volume1
# mount /dev/sdb /volume1
I get a message indicating /dev/sdb is already mounted or /volume1 is busy

So I try the following:
# mount /dev/sdb1 /volume1
Great, that works but all I see is the contents of /boot.  I unmount.

# mount /dev/sdb2 /volume1
This gives me:
mount: you must specify the filesystem type

# mount /dev/sdb3 /volume1
This gives me:
mount: unknown filesystem type 'LVM2_MEMBER'


So what gives?  This is a standard server install.

If it helps, here is my fdisk -l output:
(Note: I'm trying to clone from /dev/sdb to /dev/sdc)

root@ubuntu:/# fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 53.6 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f97c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32        6527    52179120    5  Extended
/dev/sdb5              32         124      746991   82  Linux swap / Solaris
/dev/sdb6             125        6527    51432066   8e  Linux LVM

Disk /dev/sdc: 53.6 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table



Thanks so much for any assistance you can send my way!

---

### Post by dis-abled on 2007-11-12
Hi,

I have the same problem. It looks like for some reason the Live CD install routine does not recognize LVM volumns.


I downloaded the Dapper Alternative CD and next I am going to try upgrading to Faun, then Gutsy. Watch out if you try the same thing using the default download page (It gives you the standard desktop version even if you check off the little box for the alternative CD, very frustrating).

To complicate matters sometimes the text installer can choke on pre-existing LVM names.

Good luck

---

### Post by malibu on 2007-11-13
Do you expect that this will work after you upgrade to Gutsy?

---

### Post by malibu on 2008-01-03
Incidentally, I eventually got this to work with the live CD.  Just go to the prompt and as root (or prefixing sudo on each command) do the following:

# apt-get install lvm2
# modprobe dmmod
# vgscan
# vgchange -ay <VG NAME>

Then do anything you want with it.  It needs to be done after every live CD boot, of course; but it works quite well.

---

