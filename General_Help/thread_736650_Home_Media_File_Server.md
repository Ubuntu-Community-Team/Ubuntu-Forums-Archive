---
title: "Home Media File Server"
date: 2008-03-26
forum: General Help
---

### Post by broth420 on 2008-03-26
I recently purchase a Dell Power Edge 2900 server with Perc6 RAID card and 8 750GB hard drives.  I am planning on setting it up to be basically a file server, serving flac, mp3, pictures, documents, and .vob files to another htpc.  My question is this.  What file system would be best for my 5.25TB RAID array.  I am using a 75GB Raptor for /, /var, /home/, /boot, and swap.  so the entire RAID array will be available for storage.  I am going to call this partition /media.  It is possible the file server will be accessed by several machines at once, and it will be connected to a UPS.
Thanks in advance.

---

### Post by fjgaude on 2008-03-27
If you use the card for hardware raid I'd follow the instructions on what the maual for the card suggests as to filesystem.

I have no experience with such large arrays. Under Ubuntu you have choices but as to which would be "best" is hard to say. We can see that gparted can detect jfs, reiserfs, ufs, xfs. It is full-featured on ext2/3 and reiserfs. Such tells us something.

I'd do a google on jfs, ufs, and xfs and compare to ext3 for features. It'll not be easy because so much depends of what you are looking for, as there will likely not be a "best" filesystem.

Let us know what you decide.

---

### Post by phrawzty on 2008-03-27
> **broth420 said:**
> I recently purchase a Dell Power Edge 2900 server with Perc6 RAID card and 8 750GB hard drives.  I am planning on setting it up to be basically a file server, serving flac, mp3, pictures, documents, and .vob files to another htpc.  My question is this.  What file system would be best for my 5.25TB RAID array.

Assuming that your raid care will handle the specifics of striping / mirroring / grouping / etc.. (i.e. whichever raid level you choose to go with), then - in theory - the file system you put on top of that doesn't matter too much.

That said, you should be aware of two things for any file system you choose to go with :
[LIST]
[*]Max size of a single file
[*]Max size of a partition
[/LIST]
The [Wikipedia article for ext3]("http://en.wikipedia.org/wiki/Ext3fs"), for example, notes that these values change depending on the block size you choose; in your case, you'd need to set your /media partition to use (at least) 2K-blocks at format time.  This is not normally a problem, since 2k or 4k blocks are quite normal, and supported by mkfs. :)

---

### Post by fjgaude on 2008-03-27
The default block size in ext3 is 4K, which points to file size max of 8G, if memory serves me. <smile>

---

### Post by articpenguin on 2008-03-28
ext3 has a max volume size of 8TB and 2TB single file size with 4kb.

---

### Post by fjgaude on 2008-03-28
Thanks for bringing my memory up-to-date... these terabyes are something I get confused with giga... <smile>

---

### Post by FluffyElmo on 2008-03-28
I'd definitely check out ZFS. It's been designed for storage appliances and has lots of nice features including on the fly check-sums, cloning, encryption and easy volume manipulation. The only real con is by design it gives up some CPU cycles in favour of increased functionality and data integrity, but given your system that's a more than reasonable trade-off. [http://www.opensolaris.org/os/community/zfs/]("http://www.opensolaris.org/os/community/zfs/")

It isn't GPL, so generally you'd run an ext3 system partition and access the ZFS partition(s) via FUSE. Which is more or less what you were thinking anyways:)

---

