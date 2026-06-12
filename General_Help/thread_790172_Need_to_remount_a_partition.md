---
title: "Need to remount a partition"
date: 2008-05-11
forum: General Help
---

### Post by Rhapsody on 2008-05-11
This is a fairly simple problem. I've mounted a big partition (/dev/sdb1, I think) on my new PC as /data, since I didn't know what else to do with it. Now Kubuntu won't let me write to that partition without superuser privileges, and I plan to write a lot of stuff to it in the future.

So how do I mount this partition somewhere else, and where should I put it so I can write to it as a regular user?

---

### Post by HunterThomson on 2008-05-11
> **Rhapsody said:**
> This is a fairly simple problem. I've mounted a big partition (/dev/sdb1, I think) on my new PC as /data, since I didn't know what else to do with it. Now Kubuntu won't let me write to that partition without superuser privileges, and I plan to write a lot of stuff to it in the future.

So how do I mount this partition somewhere else, and where should I put it so I can write to it as a regular user?

Well you mite have some problems removing /data but I would suggest you pop in the live CD and name and format the portion as /home.

---

### Post by Rhapsody on 2008-05-11
> **HunterThomson said:**
> Well you mite have some problems removing /data but I would suggest you pop in the live CD and name and format the portion as /home.
Problem with that being that I already have a /home partition. I mounted this one as /data because of that. I've tried moving it to /mnt/data by editing /etc/fstab, but that seems to have made no difference. Kubuntu still won't let me write to it.

I know this is possible, I did it before once. But I don't really recall how.

---

### Post by HunterThomson on 2008-05-11
> **Rhapsody said:**
> Problem with that being that I already have a /home partition. I mounted this one as /data because of that. I've tried moving it to /mnt/data by editing /etc/fstab, but that seems to have made no difference. Kubuntu still won't let me write to it.

I know this is possible, I did it before once. But I don't really recall how.

I'll check my books. Ya I meen it should just be a comand to give read write permutation to your user. why not just shrink the partition down to a reasonable size?

---

### Post by sisco311 on 2008-05-11
If it's an ext3 partition, then change the owner:
```
sudo chown -R **username:username **/data
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by HunterThomson on 2008-05-11
Ok it is

sudo  chgrp -R group /data

---

### Post by Rhapsody on 2008-05-11
> **sisco311 said:**
> If it's an ext3 partition, then change the owner:
```
sudo chown -R **username:username **/data
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Yep, that did it. It's mounted at /mnt/data now, but I can read and write to it perfectly well.

---

### Post by HunterThomson on 2008-05-11
> **sisco311 said:**
> If it's an ext3 partition, then change the owner:
```
sudo chown -R **username:username **/data
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Aw, beet me to it....

---

