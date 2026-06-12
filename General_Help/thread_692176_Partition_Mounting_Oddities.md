---
title: "Partition Mounting Oddities"
date: 2008-02-09
forum: General Help
---

### Post by vahnx on 2008-02-09
I reformatted my laptop a few months back and started by putting XP on it. Then I added Ubuntu 7.10, then just yesterday I added Vista making a triple boot. Now when I boot into Ubuntu, under Places I see liker 14.4GB Volume with a neat icon (my Vista partition), and I click it and it changes the icon to a disk drive (just like my xp partition) and it changes the name to 'disk' and add's itself to my desktop. It is nothing really that important, but it's like I have to click on the 14GB Volume icon under 'Places' in order to mount it.

Vista is 14GB Volume then disk when I click it
XP is always sda1
Filesystem is Ubuntu

Also, sometimes when I mount my External hard drive named External, it shows up as sdb1, and sometimes it shows up as External. 

Anyone know a fix to these 2 oddities?

---

### Post by taurus on 2008-02-09
After you installed Vista, did you remember to add an entry in /etc/fstab to have it mounted automatically each time you boot Ubuntu?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

