---
title: "Mount-Point error on CD/DVD"
date: 2008-04-07
forum: General Help
---

### Post by David Vincent-Jones on 2008-04-07
My CD/DVD drive appears to be unmounted and I cannot reverse the process.
When I insert a CD I get the error message " mount point /media/cdrom0 does not exist"
When I look at my media directory  'cdrom' is there (unmounted) no signs of 'cdrom0'.
I have tried "mount /media/cdrom0/" and get messege "mount: can't find /media/cdrom0/ in /etc/fstab or /etc/mtab" ... I cannot even see /etc/fstab or mtab. folders

---

### Post by matts@yoyo.org on 2008-04-07
```
sudo mkdir /media/cdrom0/  
```

should sort that out for you.

---

### Post by David Vincent-Jones on 2008-04-07
Thanks ... that solved that problem.

---

