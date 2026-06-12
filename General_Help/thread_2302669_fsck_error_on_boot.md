---
title: "fsck error on boot"
date: 2015-11-12
forum: General Help
---

### Post by jordydevoldere on 2015-11-12
I dual boot between Ubuntu and Windows 7.
I was browsing on FireFox in Ubuntu and all of a sudden I get some error message, so I reboot.
However when I try to boot into Ubuntu I get this message:
```
fsck from util-linux 2.26.2
/dev/sda6 contains a file system with errors, check forced.
/dev/sda6: Inodes that were part of a corrupted orphan linked list found.

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda6 requires a manual fsck

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```
How can I fix this? Thanks in advance.

---

### Post by ajgreeny on 2015-11-12
The simplest way is for you to boot to a live USB or DVD and from that run ```
sudo parted -l
``` to make sure partitions are still named the same way, then run ```
sudo e2fsck /dev/sda6
```assuming sda6 still is the same partition as the error message shows it to be.

If you're not sure about how to do this come back again and ask for more info.

---

### Post by jordydevoldere on 2015-11-12
When I run sudo parted -l I get "Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes. Ignore/Cancel?"

---

### Post by ajgreeny on 2015-11-12
It looks as if you can ignore that by pressing "i" and I think it should then still see the partitions.  You are not going to be writing anything to the partition table so it should not have any associated risk as far as I can see; we only want to make sure that the live system has not moved disk naming from sda to sdb, as can sometimes happen.

If sda6 looks to be the same ext4 partition of the correct expected size, run the e2fsck command as above.

---

