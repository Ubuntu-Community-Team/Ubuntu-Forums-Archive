---
title: "auto mounting fat32 drives"
date: 2008-02-07
forum: General Help
---

### Post by fhslacrosse13 on 2008-02-07
I'm having a little bit of trouble with setting up newly partitioned drives to auto mount.  I've made two partitions on my drive with hopes of one being used for data(music,videos...) and the other to run my virtual machines from.  My goal is to have them show up as drives under computer:/// along with my dvd-rw drive and filesystem with the labels of data and vmachine.  I've tried to edit /etc/fstab but I had no luck in doing so.  The fdisk -l read out is as so:
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2941    23623551    5  Extended
/dev/sda2            2942        6775    30796605    b  W95 FAT32
/dev/sda3           17348       30401   104856255    b  W95 FAT32
/dev/sda5               1         509     4088479+  82  Linux swap / Solaris
/dev/sda6             510        2941    19535008+  83  Linux


sda2 being the partition I want vmachine and sda3 for data.

---

### Post by Rocket2DMn on 2008-02-07
Can you show us your fstab file and tell us what you tried with it?  The correct fstab settings *will *have it automount on startup.

---

### Post by osos on 2008-02-07
when you tried to edit /etc/fstab did you have admin priviliges ie sudo, kdesu etc?

---

### Post by fhslacrosse13 on 2008-02-07
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=51dd192b-0cf3-47bb-9cef-1aca4c12e6bb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=4702-469A  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=13d4af70-fe7a-42bd-9a24-79015296febc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


I removed what I tried seeing as it didn't work.

---

### Post by Rocket2DMn on 2008-02-07
Your fstab has those partitions marked as ntfs, so it will give you errors, and the UUIDs may have changed, so let's try this (with sda2 and sda3 I'm assuming)
```
gksudo gedit /etc/fstab
```
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=51dd192b-0cf3-47bb-9cef-1aca4c12e6bb / ext3 defaults,errors=remount-ro 0 1
# /dev/sda2
/dev/sda2 /media/sda2 vfat defaults 0 0
# /dev/sda3
/dev/sda3 /media/sda3 vfat defaults 0 0
# /dev/sda5
UUID=13d4af70-fe7a-42bd-9a24-79015296febc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
Save the file, then mount everything in it
```
sudo mount -a
```

Here is a great guide on fstab and mounting - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
You can go with what I gave you and add the correct OPTIONS (3rd to last column where it currently says *defaults*) - ex: set the owner.

---

### Post by osos on 2008-02-07
does your /dev/sda2 mount ok? it would appear it's vfat, but being mounted as ntfs.

---

### Post by fhslacrosse13 on 2008-02-07
Thanks! That seemed to work.  But I've encountered a new problem.  I only have read-only permissions to the drives.  It says that the owner is root so I logged in as so and was unable to change this.  Is there another way to change the owner of the drive?  I'll even be willing to repartition it is needed, but when I did, under gparted, I was unable to set permissions to them.

-When I change the permission under root from read- only to read-write the changes don't save.
-I've also tried using sudo nautilus to gain access but no such luck



One other small thing that would be great to fix is that fact that every time i log in my home folder automatically pops up.  It only started doing the recently and I have no clue what I might have done to cause this.

---

### Post by Rocket2DMn on 2008-02-07
That can be fixed by adding the correct options to fstab and remounting.  For example, something like
```
defaults,o=[yourusername],rw
or
defaults,user,rw
```
Alternatively, it may also help to chown the mountpoint recursively
```
chown *yourusername:yourusername* /media/sda2 -R
chown *yourusername:yourusername* /media/sda3 -R

```
I suggest getting the correct options in fstab though.  That link I posted above is a great help, you can fiddle around with the options until it does what you want.

---

### Post by bodhi.zazen on 2008-02-07
fat does not support permissions, so the chown command will fail.

You set permissions at the time of mount, with uid=xxx,gid=yyy,umask=zzz

I suggest

uid=1000,gid=100,umask=007

This will set ownership to your admin (first) user = the group users with permissions of 770

> /dev/sda2 /media/sda2 vfat users,auto,uid=1000,gid=100,umask=007 0 0

---

### Post by macogw on 2008-02-07
wow i was just looking for this :)

i'm doing it for a flash drive since i have a minimal install and no auto-mounting and when i sudo mount it, it's root:root which means I have to sudo to put anything on the drive.  should i put "noauto" as an option?  I know "noauto" will mean that "sudo mount -a" won't do it.  If I don't put it (so it's left to basically being automount), will the comp fail to boot when the flash drive listed in /etc/fstab isn't present on boot?  Also, even though I don't have "noauto" on there, it doesn't mount when I plug it in.  I think that requires research into hald, though, right?

---

### Post by bodhi.zazen on 2008-02-07
Use "auto" for any drive you want mounted at boot. I advise "noauto" for removable devices.

Yes, automount involves hal.

On a minimal install you can consider pmount and / or an alias, personally I use a minimal install + Fluxbox + Thunar (or xfe).

---

### Post by Rocket2DMn on 2008-02-07
> **bodhi.zazen said:**
> fat does not support permissions, so the chown command will fail.

You set permissions at the time of mount, with uid=xxx,gid=yyy,umask=zzz

I suggest

uid=1000,gid=100,umask=007

This will set ownership to your admin (first) user = the group users with permissions of 770

Finally, FAT advice I can trust, thanks b.z.

---

### Post by Jose Catre-Vandis on 2008-02-18
> **bodhi.zazen said:**
> fat does not support permissions, so the chown command will fail.

You set permissions at the time of mount, with uid=xxx,gid=yyy,umask=zzz

I suggest

uid=1000,gid=100,umask=007

This will set ownership to your admin (first) user = the group users with permissions of 770

Thanks this helped refresh my memory on this one :)

---

### Post by geo909 on 2008-02-18
BTW take a look at PYSDM (PYthon Storage Device Manager). You can install it (pysdm) with synaptic/apt-get etc.

It's a GUI tool to do thing automatically without messing up with configuration files.
Once Installed, you can find it in System->Administration->Storage Device Manager.
Choose your disk/partition and click on "assistant". 
Hope that helps

---

