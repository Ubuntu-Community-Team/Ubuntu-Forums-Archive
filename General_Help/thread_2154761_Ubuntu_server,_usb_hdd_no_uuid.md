---
title: "Ubuntu server, usb hdd no uuid?"
date: 2013-06-15
forum: General Help
---

### Post by Higgins909 on 2013-06-15
Not sure if this is the best place to post this, but...

Just got a old usb hdd from a gsale and formated it using win7 ntfs and then decided to use it on my server,
it had a pretty short uuid, but I thought I would reformat it as ext3, but now it does not have a uuid

Ive tried

sudo blkid /dev/sdd1    (the name of the partition and returns nothing)
sudo blkid returns my swap my boot hdd and my other 2 internals but not this external :/

I want to automount this using fstab, but without a UUID the disks get mixed up (had this happen with my other 2 internals found out about UUID and fixed)

Thanks,
Higgins909

---

### Post by Cheesemill on 2013-06-15
Try this...
```
sudo tune2fs /dev/sdd1 -U random
```

---

### Post by Higgins909 on 2013-06-15
gah, turns out I failed to format it :/

First time
```


sudo mkfs -t ext3 /dev/sdd
```
Second time (worked)
```


sudo mkfs -t ext3 /dev/sdd1

```


Sorry, but
Thanks,
Higgins909

---

