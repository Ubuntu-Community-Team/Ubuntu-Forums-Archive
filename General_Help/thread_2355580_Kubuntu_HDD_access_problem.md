---
title: "Kubuntu HDD access problem"
date: 2017-03-14
forum: General Help
---

### Post by uzumakifahim on 2017-03-14
I've installed Kubuntu 16.04 on a fresh new desktop computer. Almost  everything is running smoothly, except the second partition of the  computer. Need to clarify that, there is only 2 partitions on that PC.  One for root or system installation and another for general storage  purpose (347.5 GB). Unfortunately, I can't create and paste any folders  or files in that partition. How can I overcome the issue? Please help  mates. :(

---

### Post by oldrocker99 on 2017-03-14
The partition probably belongs to root. The partition is *probably* sda2 (but you need to find out). Use **gnome-disk-utility** to make sure.

Then, enter this with your own user name. with the correct partition name:```
sudo chown username:username sdax
```

This will make the partition your own, with read-write access. I've had to do it myself a few times.

---

### Post by ajgreeny on 2017-03-14
> **oldrocker99 said:**
> The partition probably belongs to root. The partition is *probably* sda2 (but you need to find out). Use **gnome-disk-utility** to make sure.

Then, enter this with your own user name. with the correct partition name:```
sudo chown username:username sdax
```

This will make the partition your own, with read-write access. I've had to do it myself a few times.
Unless the syntax required has changed I think you will need to use command ```
sudo chown -R username:username /media/username/partitionname
``` where  **/media/username/partitionname** is the mountpoint of the partition.

Using the **sdax** nomenclature shown did not work in the past; the mountpoint was necessary.

---

### Post by uzumakifahim on 2017-03-16
Thanks a lot everyone. My issue is solved. Thanks a lot. Marking this post as solved.

---

