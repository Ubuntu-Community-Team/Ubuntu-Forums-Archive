---
title: "How do I add new partition?"
date: 2007-06-03
forum: General Help
---

### Post by padmanabh on 2007-06-03
I have 10 GB partition which I want to format to ext3 and use for Ubuntu. 
gparted does not ask me for any mount point.

How do i do this?

---

### Post by taurus on 2007-06-03
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it, _assuming_ /dev/hdb1 is the partition you have in mind.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

