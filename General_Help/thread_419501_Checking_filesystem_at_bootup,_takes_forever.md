---
title: "Checking filesystem at bootup, takes forever"
date: 2007-04-23
forum: General Help
---

### Post by mrlillo on 2007-04-23
Hi , I just installed Feisty on my pc. 
When I start ubuntu everything is okay until it says : checking filesystem. And that takes a very long time. At first I thought it had crashed, but it eventually started up, and everything seems to be running smoothly when I finally can log on. 

Does anybody know how to fix this/ disable this check.

---

### Post by meney on 2007-04-23
The problem your having sounds similar to one I was experiencing, are you by any chance running a dual boot?

The file /ect/fstab handles fsck at boot. If you edit the file, making the last entry a zero beside the mount you want to effect, will disable fsck at startup.

---

### Post by mrlillo on 2007-04-23
Yes I run a dual boot, the SATA disk is partiononed in 4, XP with ntfs, swap, ext3 and a fat32. I will trie what you said when I get home :o)

---

### Post by meney on 2007-04-24
Sounds good :)

If you have any problems, post back and I can try and help. If I am unable I'm sure there will be an adventurous soul out their who can step in ;)

---

