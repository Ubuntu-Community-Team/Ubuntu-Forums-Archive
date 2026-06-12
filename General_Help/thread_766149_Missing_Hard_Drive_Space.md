---
title: "Missing Hard Drive Space"
date: 2008-04-25
forum: General Help
---

### Post by emjay on 2008-04-25
Hi.

I'm wondering whether anyone can help me find my missing hard-drive space??

```
df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             291G  273G  3.7G  99% /
..........
```

As you can see, i'm missing about 14GB - the root partition is 291GB, of which 273GB has been used, which should leave 18GB.

Right? Maths was never my best subject!:)

---

### Post by thehighhat on 2008-04-25
> **emjay said:**
> Hi.

I'm wondering whether anyone can help me find my missing hard-drive space??

```
df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             291G  273G  3.7G  99% /
..........
```

As you can see, i'm missing about 14GB - the root partition is 291GB, of which 273GB has been used, which should leave 18GB.

Right? Maths was never my best subject!:)


Is /dev/sda1 formatted ext3?

If so, the missing space may be reserved blocks.  The default for mkfs.ext3 is to reserve 5% for root.


tune2fs -m <some number less than 5> 
  should free up those blocks to a new percentage

man tune2fs
  for help...

       -m reserved-blocks-percentage
              Set  the  percentage  of  the filesystem which may only be allocated by privileged
              processes.   Reserving some number of filesystem blocks for use by privileged pro&#8208;
              cesses  is  done  to  avoid filesystem fragmentation, and to allow system daemons,
              such as syslogd(8), to continue to function correctly  after  non-privileged  pro&#8208;
              cesses  are  prevented from writing to the filesystem.  Normally, the default per&#8208;
              centage of reserved blocks is 5%.

---

### Post by emjay on 2008-04-25
:rolleyes:
Thanks, highhat, yes it is ext3 and the maths is right, 5% of 291=14.55!

---

