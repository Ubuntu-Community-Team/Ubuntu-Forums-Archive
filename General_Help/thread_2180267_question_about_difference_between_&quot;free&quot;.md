---
title: "question about difference between &quot;free&quot; and &quot;available&quot;  hard drive space"
date: 2013-10-12
forum: General Help
---

### Post by sam_baker2 on 2013-10-12
hi, When I run System Monitor/File Systems, I see a listing for "Free" hard drive space and "Available" hard drive space.   Question: What is the difference between the two?   Subtracting "Used" from "Total"  leaves the "Free" amount. But the amount shown as "Available" is less than the "Free" amount.

---

### Post by grahammechanical on 2013-10-12
This mystery has been resolved in Ubuntu 13.10. In there the System Monitor does not make any mention of free space. It just says Total, Available, Used. But subtracting Used from Total does not equal Available. Neither does adding Used to Available equal Total. Further more Total is smaller than the partition's actual size according to the Disks utility.

We are not measuring the same things and we are using different measuring rods.

System folders are variable in size. They have to be otherwise the OS would stop working. The free space inside a system folder is not measured as part of free/available space on the partition. It is not available space in the context of data storage. If the amount of partition space falls below 1GB or there about we will get out of disk space warnings. The OS needs to vary the size of its system folders. It likes to keep some space available to itself alone and it is not happy if it is restricted in varying the expansion of its system folders.

Something similar happens with System memory (RAM) The OS reserves or caches memory just in case an application needs it. So, more memory is unavailable than that actually used by the application. The OS holds on the cache memory for a while making memory usage seem greater than it is.

This explanation satisfies me, even if it is not scientifically accurate.

Regards.

---

### Post by oldfred on 2013-10-12
Several things and not all tools report the same. So hard drive size and useable space vary.
MiB vs MB, journal and reserved space.

 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
      
 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3

    1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes

 sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

---

### Post by Doug S on 2013-10-12
I found it interesting recently when I found that virtual machines maximum allocated space doesn't get included in disk usage, only what is actually used by the VM is included. For example:```
doug@s15:~/docs-1310/ss_02/ubuntu-help/C$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/s15-root 952975268 651906816 252660084  73% /
udev                   7992964         4   7992960   1% /dev
tmpfs                  3200824      1472   3199352   1% /run
none                      5120         0      5120   0% /run/lock
none                   8002052         0   8002052   0% /run/shm
cgroup                 8002052         0   8002052   0% /sys/fs/cgroup
/dev/sda1               233191     77123    143627  35% /boot
[COLOR=#ff0000]/dev/sdb3            328299236  61508740 250113840  20% /media/newhd[/COLOR]
/dev/sdc1            115378728  94563968  14953796  87% /media/ssd_drive
``````
doug@s15:/media/newhd$ ls -l
total 61309384
-rwxr-xr-x 1 root         root  [COLOR=#ff0000]53687091200[/COLOR] Sep 30 12:27 desk_gnome.img
-rwxr-xr-x 1 root         root  [COLOR=#ff0000]53687091200[/COLOR] Sep 29 09:09 desk_ss2.img
-rwxr-xr-x 1 root         root  [COLOR=#ff0000]53687091200[/COLOR] Sep 26 11:46 desk_ss32.img
-rwxr-xr-x 1 libvirt-qemu kvm  [COLOR=#ff0000]107374182400[/COLOR] Oct 12 08:08 desk_ss.img
drwxrwxrwx 2 root         root         4096 Sep 10 11:16 doug  [COLOR=#ff0000]<<< Ignore, it's pretty much empty[/COLOR]
drwx------ 2 root         root        16384 Sep  1 15:08 lost+found
```Adding those file sizes would be 80% used, whereas the disk only shows 20% used.

---

