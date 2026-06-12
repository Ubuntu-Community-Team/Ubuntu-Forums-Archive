---
title: "Mount NTFS 4T hard drive"
date: 2017-12-07
forum: General Help
---

### Post by jose383 on 2017-12-07
I'm trying to mount an internal hard drive, since ubuntu does not mount it automatically, but I do not get it, it leaves some captures of what I've tried in case someone sees some solution. Ideally, it would be mounted automatically at the beginning of the system, that's it I would do it with fstab, the problem is that I can not mount it.
[https://ibb.co/nhnzCw](https://ibb.co/nhnzCw)
[https://ibb.co/kTzkkG](https://ibb.co/kTzkkG)

---

### Post by Holger_Gehrke on 2017-12-07
Just google "Microsoft Logical Disk Manager". It's similar to Linux's "Logical Volume Manager". There's something called ldmtool which can give you access to the data.

Holger

---

### Post by jose383 on 2017-12-07
Find nothing
[https://ibb.co/ne3FkG](https://ibb.co/ne3FkG)
[https://ibb.co/fGr7zb](https://ibb.co/fGr7zb)

---

### Post by Holger_Gehrke on 2017-12-07
If you don't tell it where to search, it won't find anything. Try 'ldmtool scan /dev/sdb'. A short explanation of how to proceed can be found on [stackoverflow]("https://stackoverflow.com/questions/8427372/windows-spanned-disks-ldm-restoration-with-linux#22108676") (it's the first listed answer to the question, the accepted one (further down on the page) is much older and shows a rather difficult way to do it without ldmtool)

---

