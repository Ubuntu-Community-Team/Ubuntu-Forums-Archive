---
title: "gone mad"
date: 2007-01-06
forum: General Help
---

### Post by kaiwan on 2007-01-06
Installed ubuntu 6.10 and worked fine. And now I cant assess anything on system->administration, nothing happens on mouse click, and ADD/REMOVE stopped working, it ignores Internet connection and new software I want to install???

---

### Post by taurus on 2007-01-06
What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
(use the same password that you are logged in with...)
```

---

### Post by kaiwan on 2007-01-07
thanks, will try...

---

### Post by kaiwan on 2007-01-07
When I type sudo aptitude update i get the message: "must be setuide to root", but when I type without sudo, just aptitude update, i get the the package reading...and seams to be no error....

---

### Post by taurus on 2007-01-07
What's the output of this command from a terminal?

```
groups
```

---

### Post by kaiwan on 2007-01-07
well....i have installet it again and works now :) I was messing with permissions ... and did something wrong....I have an external hard...and mount only as read only...and I want as write as well ?

thanks :)

---

### Post by taurus on 2007-01-07
What is the filesystem on that external harddrive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kaiwan on 2007-01-07
nfts file sistem

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by taurus on 2007-01-07
That would be lower case letter l as in larry...

```
sudo fdisk -**l**
```

---

### Post by Hendrixski on 2007-01-07
sounds like the account you're logged in as might not have the correct privileges to install stuff?  try logging in as a different one, perhaps one that is in the sudoers group?

---

