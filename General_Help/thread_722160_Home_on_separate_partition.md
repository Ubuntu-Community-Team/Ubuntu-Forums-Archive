---
title: "Home on separate partition ?"
date: 2008-03-12
forum: General Help
---

### Post by gibbylinks on 2008-03-12
When I installed Gutsy I thought I had given home a separate partition. I can see it in windows, but how can I check I'm using it in Ubuntu ?

Cheers

---

### Post by NightwishFan on 2008-03-12
in a terminal type:
```
sudo fdisk -l
```

---

### Post by sisco311 on 2008-03-12
and check if the partition is mounted
```
mount
```The output should be something like this: 

> ...
/dev/sdaX on /home type ext3 (rw)
...

---

### Post by gibbylinks on 2008-03-12
Thanks Guys. Yes I'm using it !! Made a note of the dev number for when I upgrade to Hardy. I've not managed yet to upgrade without flattening the drive and re-installing !!

Cheers :popcorn:

---

