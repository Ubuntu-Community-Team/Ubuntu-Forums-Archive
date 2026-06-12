---
title: "RAID 0 Help - How do I undo this?"
date: 2007-03-29
forum: General Help
---

### Post by nchase on 2007-03-29
Earlier tonight I decided I wanted to create a raid 0 array on my server. It has two hard drives. I'm unfamiliar with raid commands, and using mdadm I tried to make them into one striped logical disk. 

Apparently this failed, as I cannot see any of my disks in either normal or raid modes.

How can I fix this and make this raid 0 work? Alternatively, how can I go back to two disks instead of one single raid disk? The system still boots and everything, so I don't think I've messed it up too bad.

Here's the command I used to try to make the raid 0:
```
mdadm --create /dev/md0 --auto=yes --level=0 --raid-devices=2 /dev/hdc4 /dev/hdd1
```

---

### Post by nchase on 2007-03-30
Do I need to be more specific?

---

### Post by fanatik on 2007-03-30
can you paste in the output of:

sudo fdisk -l

---

### Post by nchase on 2007-03-30
Thanks for offering help, but I found my own solution; I just formatted the drives and decided to start from **scratch** with a raid0 configuration.

---

