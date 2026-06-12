---
title: "slow speed of harddisk after bittorrent - is defragmentation needed?"
date: 2008-06-14
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-06-14
i use my machine as a bittorrent slave 24/7. recently i found out the r/w speed of the partition i assigned for bittorrent is very slow ~6MB/s. but my /home partition is fast -50MB/s. Is defragmentation needed?
here's my partition table:
sda is for xp while sdb is for ubuntu. 
/sdb6 /data is for bittorrent
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb7              15G  4.5G  9.1G  33% /
varrun                379M  224K  378M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  112K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb8             114M   23M   86M  21% /boot
/dev/sdb6             112G   47G   60G  44% /data
/dev/sdb5              19G   11G  7.4G  59% /home
/dev/sda1              20G   13G  7.0G  64% /media/sda1
/dev/sda5              19G   16G  3.1G  84% /media/sda5
/dev/sda6              19G   11G  8.2G  57% /media/sda6
/dev/sda7              20G   17G  3.3G  84% /media/sda7
```

---

### Post by bingoUV on 2008-06-14
I am assuming ext3 filesystem.

I don't know what you mean by slave, but if it keeps downloading through bittorrent, you might use the bulk pre-allocation of filesystem space before the downloading starts. Most bittorrents support this. If you are starting to download a file of 4GB, it will allocate 4GB of disk space to the file before downloading a single byte. This prevents fragmentation.

That said, there should not be any significant fragmentation in a filesystem only 59% full even if you do not follow above steps. If you still suspect fragmentation, boot from a live CD and force filesystem check for /dev/sdb5 like
```

sudo fsck.ext3 -f /dev/sdb5

```

This will tell you how much is non-contiguous file allocation on the filesystem. Upto 15% should be handled without much performance degradation. A simple way to defragment is, from a live CD, mount it, move the data elsewhere and move the data back to the partition.

---

### Post by afeasfaerw23231233 on 2008-06-14
yes, it is ext3.
it is a slave because 80% of its uptime is for bittorrent. and i am supposed to be its master (joking).
last week i just deleted some useless files so it's only half full now. i need to delete some old files again until it fill up the 110G in about three weeks. but i notice a significant speed degrade in r/w. when i duplicate a 1G file in sdb6 it's only 6MB/s according to gkrellm, almost 8 times slower than in sdb5. it's strange if it is not caused by fragmentation.
thanks for the advice but is there a simple utilty for ubuntu like the defragmentor in xp. i also heard that linux doesn't need defragmentation somewhere in ubuntuforums. i will burn a live cd when i have time.

---

### Post by bingoUV on 2008-06-14
Most likely it is not due to fragmentation but some other reason. If you do not have a live CD, don't waste plastic by burning one. You can at least figure out how much the disk is fragmented in the following way : 

Logout. Do ctrl-alt-F1. Enter your usual login and password. Now
```

cd /root
sudo umount /home
sudo fsck.ext3 -c -f /dev/sdb5

```

Do the third command (fsck) only if there is no error in the second command (sudo umount).

I added the -c option to check for bad blocks on this partition. It will take some time. At the end of this, you will see the fragmentation report for the partition, as well as bad blocks report.

---

