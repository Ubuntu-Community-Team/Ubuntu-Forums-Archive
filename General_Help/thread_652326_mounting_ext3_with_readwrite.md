---
title: "mounting ext3 with read/write"
date: 2007-12-28
forum: General Help
---

### Post by who_cares on 2007-12-28
I have a second hard drive that I formatted to ext3 and added to fstab with this line:
"/dev/sdb1	/media/Storage	ext3	defaults,user	0	2"

The problem is I don't have full write access to it. I tried chmoding the whole drive to 777 and I've tried to chown it to my name. So far I can't write to the root of the drive, but I can write to any folder in the root of the drive. I can't write to folders that are inside other folders.

I did use -R when I ran chmod and chown.

Any ideas on how to get write access to the whole drive?

---

### Post by psusi on 2007-12-28
sudo chown chown -R yourname.yourname /media/Storage should do it.

---

