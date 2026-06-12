---
title: "External Drive data recovery"
date: 2020-02-07
forum: General Help
---

### Post by flyingsolo on 2020-02-07
I have an external drive which contained video files I'd like to recover (2TB drive, about half filled).
I'd appreciate advice on best tools to use to try this. I've seen recommendations of testdisk and photrec. I thought gparted might work but it found no 'recognizable file systems' on the disk, even though it shows 932 GB as used which makes me believe the files are indeed there.

---

### Post by dragonfly41 on 2020-02-07
If you have a 2TB drive (half full) you will need some similar capacity drive into which photorec can **save** any recovered files. Or you might find that the recovery process overwrites your files.

Always have a twin device ready for such recovery operations. It is a basic rule to remember.

P.S. Here is an [old blog]("https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/") which might be helpful. Search google using phrase "Ubuntu data forensics recovery".  Testdisk and photorec are good but there are other carving tools to explore (provided that you first clone the drive you are investigating).

[https://eforensicsmag.com/course/ubuntu-forensics-w42/](https://eforensicsmag.com/course/ubuntu-forensics-w42/)

---

