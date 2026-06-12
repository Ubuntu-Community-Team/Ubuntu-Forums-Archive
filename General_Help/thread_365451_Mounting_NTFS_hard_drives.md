---
title: "Mounting NTFS hard drives"
date: 2007-02-19
forum: General Help
---

### Post by TheGames on 2007-02-19
First, here's the information on my HDs:

> Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/hdc2           16709       24792    64934730    f  W95 Ext'd (LBA)
/dev/hdc5           16709       24792    64934698+   7  HPFS/NTFS

Disk /dev/hdd: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3497    28089621   83  Linux
/dev/hdd2            3498        3649     1220940    5  Extended
/dev/hdd5            3498        3649     1220908+  82  Linux swap / Solaris

As you can see, the 2nd HD is used for Ubuntu and the 1st HD is used for Windows (hdc1 -- first partition -- NTFS) and some other junk (hdc5 -- second partition -- NTFS).
It's unable to mount hdc1 and hdc5 by double clicking on the hard drives in X. 

So I tried using this code for the 2nd HD -- first partition (thanks to *awol* on IRC):

```
sudo mkdir /mnt/wincrap

sudo mount -t ntfs -o rw,users,umask=007 /dev/hdc1 /mnt/wincrap
```

However, when I double click on the folder created (wincrap), it says I don't have permissions to view the contents? What am I doing wrong? Is there a problem with the code? :(

P.S. I'm using **Ubuntu 6.06.1 LTS**.

---

### Post by taurus on 2007-02-19
```
sudo umount /mnt/wincrap
sudo mount -t ntfs /dev/hdc1 /mnt/wincrap -o nls=utf8,umask=0222
ls -la /mnt/wincrap
```

---

### Post by TheGames on 2007-02-19
Thank you very much. I'll give it a try and could you also give me the code for the **_2nd partition_** on the 2nd HD?

Lastly, what exactly was wrong with *awol*'s code?

EDIT: Is this also the best way to mount HDs or are there better ways?

---

### Post by taurus on 2007-02-19
The best way to mount your harddrive is through /etc/fstab.  So, if you want your ntfs to be mounted automatically each time you boot Ubuntu, you need to add two entries in /etc/fstab, one for each ntfs partition, so you don't have to type them in from a terminal every single time.

Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

```
sudo mkdir /mnt/hdc5
sudo mount -t ntfs /dev/hdc5 /mnt/hdc5 -o nls=utf8,umask=0222
```

---

