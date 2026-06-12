---
title: "folder inode/directory CG4nfmpll. just appeared in Home directory and can't delete"
date: 2014-04-30
forum: General Help
---

### Post by oldguysrule on 2014-04-30
After latest upgrades a strange new folder CG4nfmpll. just showed up in my Home directory. I can't delete it and if I try it just causes the system to freeze until I reboot. managed to move it to trash but can't remove it from there either.

Ubuntu 14.04 - 64 bit

I discovered that it is listed as an inode/directory under properties. I did a find and used the following suggested removal technique calling on the inode number itself but it is still there: find . -inum 1312883 -exec rm -rf {} \;

find . -inum 1312883 -exec rm -rf {} \;    finally worked ( 5th try) and removed the folder.

---

