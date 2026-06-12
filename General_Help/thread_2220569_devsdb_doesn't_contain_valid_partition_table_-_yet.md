---
title: "/dev/sdb doesn't contain valid partition table - yet still mounts?"
date: 2014-04-28
forum: General Help
---

### Post by jimmy the saint on 2014-04-28
I have a 2TB disk (sdb) which is mounted as ext4, and works fine.

I need to move it to a new machine, though, and I just discovered something odd.

fdisk and parted both complain that sdb has no valid partition table.

It turns out that the output of "mount" is"\

    ```
/dev/sdb on /media/data2 type ext4 (rw)
```

The disk itself is mounted, not a partition.  I have a lot of large files on this drive, and backing them up is going to be an absolute pain, but I will have to do it anyway (it's mostly movies and TV).  

My question is: what are the consequences of this?  Why does it still work?  And when I move it to the new machine, is it going to be a problem?  Is it possible to add the partition table without destroying the data?  

Fdisk output:

   ```
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
    255 heads, 63 sectors/track, 243201 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000

    Disk /dev/sdb doesn't contain a valid partition table
```

There is NO partition, just a filesystem on a bare drive.  FUUUUUUUUU.........

---

### Post by oldfred on 2014-04-28
There have been several others with unpartitioned but formatted drives.
Most of them then could not remount the drive. How are you mounting it?
Some have said it is like a very large floppy drive?

And most Linux tools expect partitions. Either MBR(msdos) or gpt(GUID) works with Linux.

---

### Post by jimmy the saint on 2014-04-28
I just have the relevant line fstab to mount /dev/sdb to /media/whatever.

I am slowly copying everything over to my new raid array so that I can clear the drive and format it correctly.  

I figured out what happened originally.

This disk resulted from a ddrescue operation on a failing drive.  Apparently, the partition table did not make it, but the filesystem itself did.  Once it mounted, I never really paid attention to HOW exactly it mounted, until I went to toss it in a new server.  I am afraid that if I move it, it may not work correctly.  

Time will tell.

---

