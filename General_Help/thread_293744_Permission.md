---
title: "Permission"
date: 2006-11-05
forum: General Help
---

### Post by svzy on 2006-11-05
Im getting an error whenever I try to write to a my /media/sda7 partition. The error I get is that I don't have permission to write to the drive. I checked who was the owner and it said "root" was the owner. Is there any way I can become the owner?

Edit:
Here's a screenie of the error [http://img518.imageshack.us/img518/8813/screenshotsb3.png](http://img518.imageshack.us/img518/8813/screenshotsb3.png)

---

### Post by bulldog on 2006-11-05
With sudo you can,but is this partition a NTFS partition?

NTFS writing is not supported natively by Ubuntu.

---

### Post by svzy on 2006-11-05
How do I use sudo? btw, its ext3

---

### Post by taurus on 2006-11-05
If it's a ext3 filesystem, then you can use chmod to change permissions so you, as a regular user, can read and write to it.

```
sudo chmod 777 /media/sda7
```

---

### Post by babooka on 2006-11-05
Is this an iPod or something like that?

---

### Post by PriceChild on 2006-11-05
You might have put something incorrectly in your /etc/fstab.

Could you post it here please?

---

### Post by svzy on 2006-11-05
No, it's not an ipod and the chmod thing fixed it. Thanks a lot.

---

