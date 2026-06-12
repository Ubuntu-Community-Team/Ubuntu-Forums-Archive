---
title: "Duplicated device mount icons in computer:///"
date: 2007-06-16
forum: General Help
---

### Post by mars777 on 2007-06-16
It's a strange situation. I don't know how to explain it exactly. Everything is working but when opening the gnome computer:/// i have the RAID devices duplicated.
Seems some mount strange behavior.

Here is the image:
[**Gnome computer:///  & desktop screenshot**](http://img143.imageshack.us/img143/2959/screendu0.jpg)

I am using a dmraid setup (Nvidia raid 1). The icons with the crying faces in the computer:/// are duplicated... and shouldn't be there.
I think it's because  I have two disks with identical partitions (2 partitions per disk / 4 total - RAID 1) but the real devices are in /dev/mapper/ and are only 2 (20GB and 60GB).
Maybe ntfs-3g behaves like this ... i dunno...

This is the fstab:
```

# Proc
proc /proc proc defaults 0 0
# Root
UUID=dd667394-912c-42e5-96dc-dcf532b1272b / ext3 defaults,errors=remount-ro 0 1
# Swap
UUID=3850793f-1812-4ff8-9f33-5eacddad4bc8 none swap sw 0 0
# DVD-RW
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
# XP Data 300GB
/dev/sdc2 /media/XP ntfs-3g defaults,locale=hr_HR.UTF-8 0 0
# Reiser 20GB
/dev/sdc3 /media/Reiser-20GB reiserfs defaults 0 1
```

So, brave Linux gurus, the question is:

How to remove these two icons in excess that are generated automatically?

I'm a medium experienced user (ie i understand fstab but the gnome / udev part is still an unknown).

Cheers! :)

---

### Post by mars777 on 2007-06-17
Nobody knows the place to remove the extra icons that are created?

---

### Post by fcorades on 2007-11-17
I've the same problem, any solution ?

---

### Post by fcorades on 2007-11-21
I've found a solution to my problem.
The problems starts when i've installed dmraid in order to use the NVIDIA RAID of my mobo.
The RAID is build by two disk WD 200GB + WD 200GB created by windows XP and operative with the Media Shield software. I need to continue to use this raid ntfs with a dual boot system. Ubuntu was looking at the raid as two different device (and this was ok before dmraid installation) and when i try to write to one disk of the raid is all ok but after when i restart windows can't access the file write by ubuntu. I think because ubuntu write these data on only one disk (and this was correct).
So after the dmraid installation and after the creation on /etc/fstab of the correct entry for the nvidia raid i start to write correctly with ubuntu on the raid and windows never see others problems.
But i still see on the computer:/// with nautilus the two icon of the two raid disk and another icon of the raid. Only the last icon really exist. I check udev rules and fstab and try to disable the two duplicated icon but without success. Finally i install the softwarePyGTK Storage Device Manager ( [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)) and the two duplicated icon go away, and i check that now on the folder where are created the disk mapping by udev (with UID) are present two entry about the raid that before are missing , probably the installation of the software have rebuild some udev rules and now the problem is solved.

---

