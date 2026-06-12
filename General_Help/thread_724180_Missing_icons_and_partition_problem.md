---
title: "Missing icons and partition problem"
date: 2008-03-14
forum: General Help
---

### Post by Saxpest on 2008-03-14
Hey, 
Just reinstalled Gutsy after a few partitioning problems and when the system first loads up I have no icons on the desktop. Once I go into home and click on the windows partition it appears on the desktop. The last time i installed ubuntu the drives were already visible on startup. Just wondering why this has suddenly happened?
On a seperate note, i used GParted to shrink windows and enlarge linux but it froze whilst shrinking and corrupted the drive. It took windows a while to sort itself out and i wondered if anyone else had this problem and what you'd do to shrink windows and give ubuntu some more breathing space?
Thanks!
Dan

---

### Post by taurus on 2008-03-14
1.  Do you have an entry in /etc/fstab to mount your windows partition?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

2.  You ran gparted from Ubuntu (harddrive) or from LiveCD?

---

### Post by Saxpest on 2008-03-14
cheers for the reply dude,
i ran it from a live cd.

these were the console reponses:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        3451    27623767+   7  HPFS/NTFS
/dev/sda3            3452        4798    10819777+  83  Linux
/dev/sda4            4799        4864      530145    5  Extended
/dev/sda5            4799        4864      530113+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fa58660

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    7  HPFS/NTFS
dan@Lappy:~$

---

### Post by taurus on 2008-03-14
Do you have any entry in /etc/fstab for /dev/sda2 & /dev/sdb1?  If you don't, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sda2   /media/sda2   ntfs-3g   defaults   0   0
/dev/sdb1   /media/sdb1   ntfs-3g   defaults   0   0
```
Save it and close down gedit window.  Then, install ntfs-3g driver, create two mounpoints, and mount them.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda2 /media/sdb1
sudo mount -a
df -h
```

---

