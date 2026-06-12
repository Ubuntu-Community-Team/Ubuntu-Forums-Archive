---
title: "External SSD format confusion"
date: 2019-06-01
forum: General Help
---

### Post by ubuntini2 on 2019-06-01
Hi
On Ubuntu Mate 18.04 LTS and recently formatted a 1TB external SSD as my primary work drive.

My confusion comes from the fact that when mounted on the desktop, when I access via any finder window what appears are 2 almost identically named volumes, 1 much smaller than the other.

> 1c12311a-1dd9-4718-befd-3f1ee0d14da1
and
> 1c12311a-1dd9-4718-befd-3f1ee0d14da11 in the attached screen capture.

Can anyone tell me what is going on? Did I format incorrectly?

---

### Post by Dennis N on 2019-06-01
You're mounting it from the file manager side pane, and I think you have an extra mount folder from a previous mount. Usually caused by not unmounting it properly the first time. Normally the mount folder gets deleted when you unmount, but if you do it incorrectly, the folder remains behind. Right click on the drive icon and use the  Eject or Safely Remove option to unmount it correctly.

To fix, first, eject the drive correctly. Then delete the sticky folder.

---

### Post by HermanAB on 2019-06-02
Be sure to have the SSD sitting safely next to you and unplugged before deleting that folder...

---

### Post by oldfred on 2019-06-02
While you still get same issue with external devices, better to use labels so when automounted it has a useful name.
I normally try to remember to label when partitioning with gparted, but when I forget I use Disks (about all Disks is useful for).

My 128GB flash drive using lsblk -f:
```

NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
sdd                                                          
&#9500;&#9472;sdd1  vfat   ESP128   9E11-6BB2                            
&#9500;&#9472;sdd2                                                       
&#9500;&#9472;sdd3  ext4   root128  87aeeacb-cb19-4c11-83e1-6d853351c86e /media/fred/root128
&#9492;&#9472;sdd4  ext4   data128  ca2325ba-4967-43e7-a8cc-31d9bc27d00c /media/fred/data128
```

If not booting, it mounts two partitions as root128 and data128. ESP on flash drive has to be manually mounted as it does not seem to auto mount it.

---

