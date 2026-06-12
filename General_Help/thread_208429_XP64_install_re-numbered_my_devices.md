---
title: "XP64 install re-numbered my devices?"
date: 2006-07-03
forum: General Help
---

### Post by NinjaYeti on 2006-07-03
I've been running dapper for a while, and decided one day to re-install my xp64 version of windows. I did, and now after re-loading grub I discover that my partitions are numbered differently. Before I had my ext3 root and page file as sda3 and sda4 respectively, and now fdisk shows them as sda2 and sda3. What's up with that? Anyone know what's going on or why this would happen? 

Also, I have to modify my menul.lst file to reflect the new numbers, but any update-grub that happens in the future will put back in the old sda3 and sda4 devices. Is there some default setting somewhere that tells ubuntu which partitions it's using (I already fixed fstab)?

---

### Post by Rui Pais on 2006-07-03
Hi, give a look at [here]("http://ubuntuforums.org/showthread.php?p=1153584#post1153584").

---

