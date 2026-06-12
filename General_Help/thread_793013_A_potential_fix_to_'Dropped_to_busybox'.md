---
title: "A potential fix to 'Dropped to busybox'"
date: 2008-05-13
forum: General Help
---

### Post by MikeReiner on 2008-05-13
I stopped using linux in general when they started failing to boot. I've come to realize, that more specifically, they fail to mount partitions on my hard drive!

So I took out my 80gb WD hard drive, put a 120gb seagate in, and boom, everything works perfectly now.

So to all you getting boot errors, try installing on another hard drive!

It's odd.. that 80gb works perfectly fine with XP still..
Anybody have any thoughts on that?

---

### Post by pointone on 2008-05-14
There's a reason why it was failing to mount partitions on the drive. From my experience, the problem is usually that the UUID of the drive has changed due to formatting, resizing, kernel updates, etc., making the old entry for the drive in fstab incorrect. All that is required to fix this is updating of fstab to match the output of blkid.

Failure to mount could also be due to hardware problems or data corruption, however.

---

