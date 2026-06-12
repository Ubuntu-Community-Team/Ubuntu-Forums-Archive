---
title: "[SOLVED] Mounting a new HDD?"
date: 2008-07-04
forum: General Help
---

### Post by G1ZmO65 on 2008-07-04
OK very daft beginner question

I have added another HDD to my Ubuntu server

How do I mount it and start setting up folders on it with Webmin (or CLI)?

I think I've managed to set the partition type as its recognised in Disk and Network Filesystems as "SCSI Device B Partition 1 (Linux)"

I went in to Disk and Network Filesystems with Webmin and set it up as shown in the jpg and got the error: 
[I]"Failed to save mount : Mount failed :
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"[/I]

---

### Post by justleen on 2008-07-04
looks like there isnt a filesystem on it yet ```

mkfs.ext3 /dev/sdb1

``` 
after that you should be able to mount it

---

### Post by G1ZmO65 on 2008-07-04
Thanks justleen

Sorted :)

---

