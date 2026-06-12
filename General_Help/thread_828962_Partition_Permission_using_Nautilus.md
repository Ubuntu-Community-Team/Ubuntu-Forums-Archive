---
title: "Partition Permission using Nautilus"
date: 2008-06-14
forum: General Help
---

### Post by arpan on 2008-06-14
Hi all,

I have an additional ext3 partition that I need to mount with write permissions.

When I click on Places-->Computer, it shows the partition and when I double click on the icon it mounts the partition and opens it. However it does not allow me write anything on that partition.

In Gutsy this wasn't a problem.

I already tried to mount it using fstab in a directory with write permissions but then it does not show partitions icon in Nautilus(computer:///). So it seems there is no way to write on to that partition using Nautilus(as a partition icon and not as a subfolder in filesystem). This is my primary concern as my cousin use the same login and he doesn't know anything about mounting partitions but he needs access to that partition.

Is there any way that I can make Nautilus to mount that partition with write permission?:confused:

Thanks in advance for every bit of your help.

---

### Post by VMC on 2008-06-14
Show the  output from the following :

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

---

### Post by arpan on 2008-06-14
I've attached the outputs of the commands that you mentioned.

Thanks.

---

### Post by arpan on 2008-06-15
anyone???

---

