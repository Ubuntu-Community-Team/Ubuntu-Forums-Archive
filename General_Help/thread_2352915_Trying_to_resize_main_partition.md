---
title: "Trying to resize main partition"
date: 2017-02-16
forum: General Help
---

### Post by Always.Learning.AP on 2017-02-16
I tried to use gparted to resize my primary partition of Ubuntu. I was able to delete my swap file and create a new one with the empty space on the disk. Problem is I can't make my partition any bigger than it is even though I have empty space.

gparted also seems to have created some kind of error where my file system thinks some of it is ext3 even though it isn't.

Can some one help me fix my partition?

[ATTACH=CONFIG]273759[/ATTACH]

---

### Post by &amp;KyT$0P# on 2017-02-17
You are trying to modify mounted partitions that are part of the running OS.  As you have found out, that will not work.

Try booting a live media of Ubuntu and running gparted from there.

---

