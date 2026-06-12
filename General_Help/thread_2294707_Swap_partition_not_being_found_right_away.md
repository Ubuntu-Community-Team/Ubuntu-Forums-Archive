---
title: "Swap partition not being found right away"
date: 2015-09-12
forum: General Help
---

### Post by psfal on 2015-09-12
I was doing some partitioning to install another OS alongside my Ubuntu 14.04 and found where I'd inadvertantly made the swap partition almost 88gig. I resized it to 8gig, installed Debian on another partition and now Ubuntu keeps me waiting on boot while it looks for that swap partition. What file contains the swap drive address? Can I retrieve the address in gparted and edit the file to eliminate this issue?

---

### Post by deadflowr on 2015-09-12
run 
```
sudo blkid
```
locate the swap partitions UUID
then run
```
sudo nano /etc/fstab
```
and replace the existing UUID number for the swap line with the new one.
then you can press ctrl + x to save and exit.
> Can I retrieve the address in gparted
Alternatively, yes it'll be in the information part, if I remember right.

---

### Post by howefield on 2015-09-12
Guessing that you changed the UUID of the swap partition when you resized, meaning your fstab now points to a non existent swap.

Use..

```
sudo blkid
```

or

```
ls -l /dev/disk/by-uuid/
```

and compare the UUID for swap with what the /etc/fstab file thinks it is.

---

### Post by psfal on 2015-09-12
Perfect! Thanks very much guys :-)

---

