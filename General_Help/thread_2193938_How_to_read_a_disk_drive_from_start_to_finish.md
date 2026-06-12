---
title: "How to read a disk drive from start to finish?"
date: 2013-12-15
forum: General Help
---

### Post by KingNeil on 2013-12-15
If I wanted to read the entire contents of a disk drive, or even write to them, like, the 0s and the 1s, how would I do that...?

I'm not interested in the formatting of the drive, like, FAT or anything. I just want to be able to read and write everything on the disk, precisely, down to the 0s and 1s.

---

### Post by tgalati4 on 2013-12-15
```
sudo dd if=/dev/sda3 of=/dev/stdout
```

Control-C when you get tired.

---

