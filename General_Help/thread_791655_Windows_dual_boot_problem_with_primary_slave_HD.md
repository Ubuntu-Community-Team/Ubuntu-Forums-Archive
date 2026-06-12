---
title: "Windows dual boot problem with primary slave HD"
date: 2008-05-12
forum: General Help
---

### Post by bpv on 2008-05-12
I am new to Ubuntu/linux. I have a Dell Precision 360. I have two hard drives. Primary master is a HD I added and had Ubuntu installed. Windows XP is on old HD with slave jumper setting. when I do fdisk I can see both hard drives and master is labeled 'sda' with partitions listed and slave as 'sdb' with Dell utility and NTFS file partition listed. When I use GRUB to load up Windows XP (using popular instructions I found on the forums to edit menu.lst file) I see Dell running hardware diagnostic. Every test says 'pass' but Windows XP will not load. What might be the issue here? Can anyone help me?

---

### Post by bpv on 2008-05-12
I only had to try the 'rootnoverify (hd1,1)' option. Should have read those instructions more carefully!

---

