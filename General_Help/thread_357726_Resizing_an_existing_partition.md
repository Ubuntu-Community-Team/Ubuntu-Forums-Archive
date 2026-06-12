---
title: "Resizing an existing partition"
date: 2007-02-10
forum: General Help
---

### Post by McLeod on 2007-02-10
Hello,

I am dual booting Ubuntu with Windows XP. XP is set up on a FAT32 partition. I would like to allocate more size to my XP partition, as I store a lot of my multimedia there. What is the easiest way to do this? Below is the output I get from fdisk.

Thanks!

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       50790    25598128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           50793      113555    31631985   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          113555      116280     1373557+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          113555      116280     1373526   82  Linux swap / Solaris

```

---

### Post by dcstar on 2007-02-10
> **McLeod said:**
> Hello,

I am dual booting Ubuntu with Windows XP. XP is set up on a FAT32 partition. I would like to allocate more size to my XP partition, as I store a lot of my multimedia there. What is the easiest way to do this? Below is the output I get from fdisk.

Thanks!

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       50790    25598128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           50793      113555    31631985   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          113555      116280     1373557+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          113555      116280     1373526   82  Linux swap / Solaris

```

You may be able to do this with the Live CD, or with the tools on specialist Utility boot CDs like this one:

[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

