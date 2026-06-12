---
title: "XP partition vanished"
date: 2008-03-13
forum: General Help
---

### Post by msquared06 on 2008-03-13
Tonight when I booted my laptop my windows partition was not mounted on my desktop anymore and I could not access it.  I haven't done any toying with Ubuntu today and I'm not sure how to re-add the partition without reinstalling Ubuntu.  Windows still boots normally.  Any help would be appreciated.  Thanks.

---

### Post by SPr on 2008-03-14
Does it reappear after a a reboot?

If it doesn't can you mount it manually?
```

sudo mkdir /media/hda
sudo mount /dev/hda1

```

---

### Post by danwood76 on 2008-03-14
It might be that an update or something has messed the UUID fro the partition.

Could you post the output of the following 2 commands in terminal please:
```

sudo fdisk -l
cat /etc/fstab

```
This will help us determine the problem, I wouldnt do what SPr said as its just a waste of time.

---

### Post by forestpixie on 2008-03-14
add this to the list

```
blkid
```

---

