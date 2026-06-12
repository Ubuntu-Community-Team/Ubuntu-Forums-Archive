---
title: "Unmount NTFS"
date: 2006-11-09
forum: General Help
---

### Post by jrsteffes on 2006-11-09
Here is what I got: I want to unmount /dev/sdb1 and then reformat it to a file system that can be used by both linux and PC.  What I realy need is the comands to unmount!  Thanks for the Help!

jason@jason-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18666   149934613+  83  Linux
/dev/sda2           18667       19457     6353707+   5  Extended
/dev/sda5           18667       19457     6353676   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

---

### Post by PriceChild on 2006-11-09
```
umount /dev/sdb1
```

---

### Post by jrsteffes on 2006-11-09
Ok it looks like it unmounted when I restarted:

jason@jason-desktop:~$ umount /dev/sdb1
umount: /dev/sdb1 is not mounted (according to mtab)
jason@jason-desktop:~$ 

but it will not let me delete the folder I mounted it in which is /media/windows it says "Cannot move "/media/windows" to the trash because you do not have permissions to change it or its parent folder."

How do I remove the folder?

Then how do I Reformat the drive to NFS I guess (I think that will work with both windows and linux).

---

### Post by PriceChild on 2006-11-09
```
sudo rm /media/windows
```Will remove the folder.

If this doesn't work... MAKE SURE ITS NOT MOUNTED then check inside for any files/folders. If you don't need anything inside then```
sudo rm -R /media/windows
```Fat32 works with linux and windows... also an ext3 partition will work with both if you install [http://fs-driver.org](http://fs-driver.org) on the windows install.

---

### Post by taurus on 2006-11-09
```
sudo rmdir /media/windows
```

p.s.  With directory/folder, you have to use rmdir though!

---

### Post by PriceChild on 2006-11-09
> **taurus said:**
> ```
sudo rmdir /media/windows
```p.s.  With directory/folder, you have to use rmdir though!Thanks :)

---

### Post by jrsteffes on 2006-11-09
Thanks that did it.

Now how about that format so linux can use my 2nd hard drive?

---

