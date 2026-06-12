---
title: "how do I change the partition names in the sidebar?"
date: 2012-12-01
forum: General Help
---

### Post by lunaphiles on 2012-12-01
i assigned my personal partitions numbers 1-5 when I installed, but I want the sidebar to show designations like:
1:Nature
2:Techs
3:Health
4:Society
5:Culture

I believe it has to do with the /etc/fstab, but I am not sure, and i know if it is not done properly it gets really messy to fix.

---

### Post by ohnonot on 2012-12-03
it should work with gparted:
highlight partition, unmount it, then choose partition->label from the menu.

edit: actually, forget that. my brain was off. sorry.
yes, you can tell the system through fstab where to mount a partition - afterwards it shows up like a normal folder, for which you can make a shortcut in your sidepane.

i have one extra partition and it looks like this in fsatb:> 
# /dev/sda4?
UUID=xxxxxxxxxxxxxxxxxxxxxxxxx /home/data               ext4    errors=remount-ro 0       1you have to find the uuid (one possibility is with gparted) and how the part. is formatted (ext4 in this example).
it then gets mounted to /home/data.

(side comment: i had some trouble with permissions and had to chown it.)

---

