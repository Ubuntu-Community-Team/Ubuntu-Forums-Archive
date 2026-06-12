---
title: "Tweaking hard disk for performance"
date: 2007-11-20
forum: General Help
---

### Post by SeanTater on 2007-11-20
Here is my problem: I have ~500GB of videos to edit. And until I can set my script to do otherwise, I have to make 1000's of small (about 10 sector) reads per second. (although I don't know how much a sector is..) I have a 7200 rpm sata hard drive with 16MB cache, formatted XFS. I added noatime, which approximately improved the speed by a factor of 3. Is there a way to speed this up some more?

---

### Post by 1/0 on 2007-11-20
Well, I haven't used XFS much (I'm old fashioned and like EXT3) but there are some tweaks (except RAID). The fstab options for one: noatime,nodiratime,logbufs=8

[LVM]("http://www.tldp.org/HOWTO/LVM-HOWTO/") for a second, hdparm for a third. Also, XFS apparently fragments (!!?!) and needs defragmenting from time to time. With xfsdump installed check if defragmenting is needed by:

```

sudo xfs_db -r /dev/sdXY

```

Defragment by:
```

sudo xfs_fsr -v /dev/XY

```

That's something... Also I googled this:

[http://www.everything2.com/index.pl?node_id=1479435](http://www.everything2.com/index.pl?node_id=1479435)

---

### Post by SeanTater on 2007-11-20
Okay -- I have no RAID. And unfortunately, I don't see how LVM speeds up a single drive (though it might be cool if I had multiple). hdparm does not give me much information, but it says that it's for IDE drives and mine is SATA. sdparm seems to be for SCSI..

I'll check the fragmenting on my next opportunity to unmount it (a few hours at least), but the contents change completely every few days and the files are huge so I figure there are large tracts of empty space to write in consecutively.

I'll read that webpage next time I get a chance..

---

### Post by newlinux on 2007-11-20
> **SeanTater said:**
> Okay -- I have no RAID. And unfortunately, I don't see how LVM speeds up a single drive (though it might be cool if I had multiple). hdparm does not give me much information, but it says that it's for IDE drives and mine is SATA. sdparm seems to be for SCSI..

I'll check the fragmenting on my next opportunity to unmount it (a few hours at least), but the contents change completely every few days and the files are huge so I figure there are large tracts of empty space to write in consecutively.

I'll read that webpage next time I get a chance..

Just an FYI:
XFS filesystems can be defragged while mounted.

---

### Post by malfist on 2007-11-20
I would recommend JFS, it's fast, good for small files and is less CPU intensive than any of the other common file system. JUST DON'T USE EXT2/3

---

### Post by SeanTater on 2007-11-20
I didn't know they could be defragged while mounted, cool! I see JFS, but I think for my purposes, XFS is close enough.. (most of the benchmarks I've seen set them side-by-side for what I'm using).

I'm no expert, but shouldn't caching guess sequential reads, reading 5-10MB instead of on the order of kilobytes at a time, or is there a way I can configure that? I've normally got 1-1.5 GB of disk cache in memory, so it should have room, right?

---

### Post by bingoUV on 2007-11-20
Most filesystems let you adjust block size. I assume you have large files from which you make large sequential reads. In which case large block size should help performance.  Default block size is optimized for the typical file size / read quantum.

---

### Post by SeanTater on 2007-11-20
mkfs.xfs says that can only be increased to 64k or my linux pagesize. How can I tell what my pagesize is?

---

### Post by SeanTater on 2007-11-20
Humph. It's already at my pagesize, which is 4k.

---

### Post by SeanTater on 2007-11-21
Is there some way I can adjust page size or block size other ways? Right now, I'm only getting about 25MB/s when hdparm says I should be able to get 79MB/s. (Besides, it's fun tweaking it)

---

### Post by bingoUV on 2007-11-21
How did you figure out your page size? Someone here might be able to get some hint from there and help.

---

### Post by SeanTater on 2007-11-21
There is a C function that returns the pagesize, which is appropriately, getpagesize(). So I had it simply print that number, which was 4092. (which is 4 kilobytes)

---

