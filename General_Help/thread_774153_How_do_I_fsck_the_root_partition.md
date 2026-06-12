---
title: "How do I fsck the root partition ?"
date: 2008-04-29
forum: General Help
---

### Post by busgeek on 2008-04-29
My old laptop has developed a nasty filesystem error on the root "/" (ext3) partition and exist fsck with a return code of 8 - suggesting I do a manual fsck instead - when the partition is not mounted. 

I guess I can use a live-CD to get a shell prompt and then run the fsck from there.  But of course, the fstab is listed on the root partition so when I try:

  $ fsck /dev/hda3

It doesn't actually know where that partition is...

So I'm obviously missing a step.   But what!?

Thanks!

---

### Post by damis648 on 2008-04-29
when you get to the GRUB, select Ubuntu Recovery Console and when you boot and enter it, just type 

```
fsck
```

and see if that works.

---

