---
title: "Stop fsck running at startup"
date: 2007-04-05
forum: General Help
---

### Post by james016 on 2007-04-05
Hi all

Have just installed Ubuntu on to my laptop. However it takes ages to boot up as it performs a fsck on the partitions or that is what appears on the screen. It does this every time. Is there a way of stopping this running as it is quite annoying?

Thanks

---

### Post by Martje_001 on 2007-04-05
fsck checks your hard disks for errors. Maby you can run fsck after booting, so the errors disappear.

---

### Post by josephus on 2007-04-06
Modify /etc/fstab

basically the sixth field (fs passno) for each device controls whether or not fsck is run for a particular partition.  

For example here is part of my /etc/fstab (slightly edited so things fit on one line)

```

# /dev/hda6
UUID=xxxx   /    ext3   defaults,errors=remount-ro         0        1
# /dev/hda1
UUID=yyyy  /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46      0       0

```

/dev/hda6 this is my root partition and the sixth field should be set to 1
/dev/hda1 contains my windows stuff the sixth field is by default set to 2, which tells to fsck to scan the drive.  Setting it to zero causes fsck to skip the partition.

This information is detailed in the man pages.

---

### Post by jongkind on 2007-04-06
There is an excellent script called fsckdown that you can use to run fsck  when you shutdown your computer. Look at the Wiki:

[https://wiki.ubuntu.com/fsckdown?highlight=%28fsck%29]("https://wiki.ubuntu.com/fsckdown?highlight=%28fsck%29")

---

