---
title: "Gparted - how to make it work"
date: 2005-07-14
forum: General Help
---

### Post by davegahan on 2005-07-14
Cant manage to resize my partition and make a new one. All entries to perform the operations are grey and cannot be accessed. The FAQ on the programs website claims the partition to be manipulated must be umounted first, but, I can't do that because the partition is marked as "busy".
How can i resize partitions using Gparted ?

---

### Post by badrinarayan on 2005-07-14
You can't use gparted on an active partition. If you are booting from another partition or hard disk, you may resize it. Your best bet would be to use a live cd (like knoppix) with qtparted or gparted (unfortunately I am afraid ubuntu live does not have these)

Regards
Badri

---

### Post by davegahan on 2005-07-15
Thank you for the answer. That makes gparted useless on a workstation then. Is there anyway to resize active partitions - like partition magic does in windows ?

---

### Post by badrinarayan on 2005-07-15
AFAIK no :(
I don't think Partition Magic Resizes live partitions too. It does them when you restart right? Now, QtParted can do that when you boot off a live cd (like the handy Knoppix / MEPIS)  and I think it is considerably faster. I wouldn't know for sure as it was a long time since I used Partition Magic.

Regards
Badri

---

