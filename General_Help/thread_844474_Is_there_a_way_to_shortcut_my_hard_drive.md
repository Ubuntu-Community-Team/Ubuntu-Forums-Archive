---
title: "Is there a way to shortcut my hard drive??"
date: 2008-06-29
forum: General Help
---

### Post by morbid_bean on 2008-06-29
After setting up ntfs-config I finnally am able to access my hard drive but only by manualy going to Filesystem>media> then the hard drive..........i was wondering if there was a way i could put a shortcut on my desktop...or in my places menu or something..

---

### Post by Rocket2DMn on 2008-06-29
Is this drive internal or external?  Can you please post
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

---

### Post by morbid_bean on 2008-06-29
> **Rocket2DMn said:**
> Is this drive internal or external?  Can you please post
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb00bb00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2310    18555043+   7  HPFS/NTFS
/dev/sda2            2311        4864    20515005   83  Linux
/dev/sda3            4865        4865        8032+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
180 heads, 63 sectors/track, 27564 cylinders
Units = cylinders of 11340 * 512 = 5806080 bytes
Disk identifier: 0xd3c7f331

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23671   134212648+   7  HPFS/NTFS

```


I acutally have 2 hard drives...one 40gb split in half w/ xubuntu and winxp on it...and an extra slave 130gb drive w/ extra stuff on it (music,videos,documents, etc.....)

---

### Post by Victormd on 2008-06-29
> **morbid_bean said:**
> After setting up ntfs-config I finnally am able to access my hard drive but only by manualy going to Filesystem>media> then the hard drive..........i was wondering if there was a way i could put a shortcut on my desktop...or in my places menu or something..

Check the link on my signature on How to automount drives.

---

### Post by morbid_bean on 2008-06-29
i get this at this part...

```
sudo gedit /etc/fstab
sudo: gedit: command not found

```

---

### Post by Rocket2DMn on 2008-06-29
Yes, you should just need an Fstab entry for the internal hard drive.  See these links, too:
[uhelp]community/Fstab[/uhelp]
[uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp]
Basically you just need to create the mount point, add the fstab entry, then remount.

---

### Post by Rocket2DMn on 2008-06-29
> **morbid_bean said:**
> i get this at this part...

```
sudo gedit /etc/fstab
sudo: gedit: command not found

```

Try just using nano which is a terminal based editor
```
sudo nano /etc/fstab
```
gedit isn't available in Xubuntu apparently.

---

### Post by WRDN on 2008-06-29
If you want a shortcut, isn't it possible to just create a launcher to open the folder in the media directory?
(Right Click and select New Launcer, or something similar)

---

### Post by Rocket2DMn on 2008-06-29
> **WRDN said:**
> If you want a shortcut, isn't it possible to just create a launcher to open the folder in the media directory?
(Right Click and select New Launcer, or something similar)

Yes, you can create a symlink to the directory, but it's not quite the same (it will show the path as the symlink, not the true mount point).

---

### Post by Victormd on 2008-06-29
> **morbid_bean said:**
> i get this at this part...

```
sudo gedit /etc/fstab
sudo: gedit: command not found

```

gedit is for ubuntu. If you're using **Kubuntu**, replace gedit with **kate** and if you're using **Xubuntu**, replace gedit with **mousepad**.

---

### Post by morbid_bean on 2008-06-29
i did your guide and i get some    " no final newline at /etc/fstab "  "devices or resource busy"  or something like that dury boot...it only gives me a few seconds to read

---

### Post by morbid_bean on 2008-06-29
bump! :)

---

### Post by morbid_bean on 2008-06-29
bump!

---

### Post by Rocket2DMn on 2008-06-30
Did you follow the links I posted before or are you following Victormd's link?

---

### Post by FAttyBones on 2008-12-17
A three step process that will help you (if you're using xubuntu)

1: set up your /etc/fstab

search "how to fstab" on google if you don't know how

You can skip step 1 if your drives already auto-mount.


2: Find the folder in /media that corresponds to your drive and drag it with the mouse into the left panel.  This will put it in your places menu too.

3: Unfortunately this will not put it on your desktop.  I am told that this is not a bug.  You can write scripts containing a line like 
"thunar /media/name-of-your-partition" and place those in your ~/desktop folder if you wish.  A script is just a text file containing teminal commands.  I chose not to do step 3 myself.

hope this helps.

---

