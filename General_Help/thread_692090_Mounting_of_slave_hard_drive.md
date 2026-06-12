---
title: "Mounting of slave hard drive"
date: 2008-02-09
forum: General Help
---

### Post by HEN*K on 2008-02-09
Hi!

I just installed Ubuntu 7 on my computer because i have been using an older version up until now. My problem is that I have a hard drive that i can't mount. It is an ntfs-drive which has been mounted in Ubuntu before but I can't remember how i did it last time. All my music and my movies are on that drive so I would really like to be able to access it. If anyone could help me with this i would be really grateful...

Thanks...

/ Henke

---

### Post by taurus on 2008-02-09
Assuming the drive is /dev/sdb1, open a terminal and run

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o umask=0222
df -h
```

---

### Post by HEN*K on 2008-02-09
Thanks. Will this auto mount the drive each time I turn on the computer or do I have to mount it every time i want to access it?

---

### Post by taurus on 2008-02-09
If you want to mount it each time you boot Ubuntu, then you need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ntfs-3g   defaults   0   0
```
Again, assuming your ntfs partition is /dev/sdb1.  Save it and then install ntfs-3g driver for it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

---

