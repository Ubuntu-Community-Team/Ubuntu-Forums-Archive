---
title: "Music player can't access partition in separate drive :("
date: 2016-11-28
forum: General Help
---

### Post by javierdl on 2016-11-28
Hi all,

I am using Tomahawk. It can access the music files in my External USB drive just fine. But it won't access a partition in an internal drive.
I suspect this has to do with permissions, doesn't it?
Last month Bashing-om was kind enough to help me with a [similar situation]("https://ubuntuforums.org/showthread.php?t=2339524"), creating a mounting point in a partition in an internal drive to install games from Steam. Would I need to do the same this time?

Thanks guys,

JDL

---

### Post by Dennis N on 2016-11-28
I access and play music files stored on a data partition on a 2nd internal hard drive from my player (audacious). To do this, the data partition on the 2nd drive is mounted in fstab at startup, and I have made myself the the owner of the file system on the data partition. If you do the same, it should work fine.

---

### Post by javierdl on 2016-11-29
Thank you Dennis N, I'll look into it.

JDL

---

