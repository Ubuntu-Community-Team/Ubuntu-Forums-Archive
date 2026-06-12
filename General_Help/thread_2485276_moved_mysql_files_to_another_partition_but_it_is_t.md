---
title: "moved mysql files to another partition but it is twice the size"
date: 2023-03-25
forum: General Help
---

### Post by hakan439 on 2023-03-25
Hi. I bought a new faster name disk and moved mysql files to that disk on Ubuntu. I successfully configured the db but it consumes twice the size of db. 
mysql files are in folder called DB/mysql on the new name disk. When I check the size, it is 40G

the name of the folder is DB under media
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291952&stc=1[/IMG]

and it has 40GB
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291953&stc=1[/IMG]


name disk is a 1 TB disk but it shows ~90 GB of usage. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291951&stc=1[/IMG]

---

### Post by TheFu on 2023-03-25
Check that the original files weren't "sparse".

---

### Post by Holger_Gehrke on 2023-03-25
There are a few uses of space which would account for the difference depending on the file system you are using. On ext[234]-filesystems 5 % of total capacity are reserved for root by default to prevent system lock ups on filled file systems (actually only makes sense for the root file system or the one containing /var if you've put that on a separate fs; you can change the amount of reserved space using tune2fs); the file system itself also uses quite a bit of space (superblock(s), inode tables, free inode list, directories ...).

Holger

---

