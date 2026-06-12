---
title: "Cannot Read NTFS drive."
date: 2008-02-08
forum: General Help
---

### Post by endlesslydevoted on 2008-02-08
Alright so I am kind of a noob to Linux. So please excuse me if I am not exactly sure how to do everything. I have an external hard drive that has an HFS+ partition and an NTFS partition. I want to open some files from the NTFS partition, I don't really care much about writing to the drive in Linux. When I first installed Ubuntu it detected my NTFS partition and put it on the desktop. I clicked on it and noticed I could access it. I was a bit excited, but I decided to update Ubuntu. After the update finished it gave me an error when I tried to open the drive from VLC Media player, so I attempted to go to the desktop and click on the drive, and it didn't do anything. So I searched google and decided to try some of the ntfs3g methods to getting it to work. Again I was not so great at the whole terminal thing since I am a noob, but after I thought I finished, I restarted the computer and the ntfs partition no longer showed up at all. The HFS one still shows up, but not the NTFS. Is there anything I can try to get it to work? Any help would be greatly appreciated.

---

### Post by taurus on 2008-02-08
Try to mount it from a terminal to see what the error message is.  99.99% of the time it would probably complain about how you didn't shut it down cleanly so you need to connect it back to your windows and go into removing the device first before you unplug it.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by endlesslydevoted on 2008-02-09
So when I typed in the first line of code you gave me, I got this.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf92ff92f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bab57

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3493    28057491   83  Linux
/dev/hdb2            3494        3649     1253070    5  Extended
/dev/hdb5            3494        3649     1253038+  82  Linux swap / Solaris
```

My 250gb external drive is not listed in that list anywhere, however when I type the next bit of code, I get this. 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              27G  2.7G   23G  11% /
varrun                503M   88K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M  100K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   38M  466M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1              75G   67G  7.6G  90% /media/disk
/dev/sda1              11G  6.5G  3.6G  65% /media/Leopard
```

If you look at the bottom, /dev/sda1 is one of the partitions on my 250gb external hard drive. So it looks like Linux isn't detecting my ntfs drive at all.

Any other ideas? I am a bit clueless at this point.

---

