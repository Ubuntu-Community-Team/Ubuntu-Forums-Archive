---
title: "Why is Ubuntu Disks showing different space size numbers than df -h?"
date: 2022-05-04
forum: General Help
---

### Post by ailerios on 2022-05-04
Inside Ubuntu's GUI tool Disks, my device "/dev/nvme0n1p4" is reading: "124 GB &#8212; 7,3 GB free (94,1% full)", suggesting that there are still 7.3GB left on the partition.
If I get the list with df -h, I'll get this line:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p4  114G  107G 1001M 100% /

```

1GB does not equal 7.3GB, if I'm thinking correctly.
I just emptied my trash, before I had under a GB of space left and the system warned me about low space on Root. Because of the numbers inside Ubuntu Disks, I always thought I'd have a lot of space free.

So, is there some free space anywhere and I just don't understand a concept how Ubuntu filesystems work, and can I use that space to resize Root so I can install more software? Or is it simply a strange error that Disks has?

---

### Post by ailerios on 2022-05-04
Ah, nevermind. I just found out that the appropriate place to look up your space is System Monitor -> File Systems. That one shows the same numbers than df -h. Alright, so that's probably what I can use. I'm still curious what the missing 6.3GB are though. I have 2GB of swap space, so maybe that's that, okay. Leaves 4.3GB.

---

### Post by Impavidus on 2022-05-04
I don't think it's the swap space. If you use a swap file, that's just a file counted as all other files, and if you use a swap partition, that's a separate partition not counted in this partition.

There are 3 issues here.
1: Some tools use MB and GB, using powers of 1000, other tools use MiB and GiB, using powers of 1024, and they aren't always clear on which of the two they use.
2: There's a difference between the size of the filesystem and the space available for storage, as there is some filesystem overhead.
3: Some space (by default 5%) on the filesystem is reserved for the root user and not available for ordinary users. df doesn't report this as available.

With tune2fs (have a look at the manual with man tune2fs) you can change the amount reserved for root, but making those final 5% available isn't very useful. If you already filled 95% of a drive, getting another 5% won't buy you much time before you filled that too. Furthermore, hard drive performance is better if you keep some space free. On spinning hard drives that prevents fragmentation, allowing for faster access, and on SSDs it allows the wear levelling to do a better job, increasing drive life.

---

