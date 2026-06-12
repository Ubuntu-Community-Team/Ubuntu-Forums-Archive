---
title: "How to create a new and mount partition in ubuntu"
date: 2008-06-29
forum: General Help
---

### Post by yinglcs2 on 2008-06-29
Hi,

i use GParted to create a new partition:
Parition: /dev/sdb3
Filesystem: ext3
Mountpoint:
size: 25 GB
Used: 374.99MB
unused: 24.78 GB

But how can i use that parition? How can I auto-mount to as start copying files there?

Thank you.

---

### Post by vikyrulz on 2008-06-29
I am not sure about how to mount the partition.. I guess when you double click the partition from the GUI it automatically mounts it..

If it doesn't then there is another way of copying files..

sudo mv loctn1 loct2..


"sudo" works fine.... try it out.. n lets wait for experts to see how to mount the partition manually...

njoy!!

---

### Post by bodhi.zazen on 2008-06-30
> **yinglcs2 said:**
> Hi,

i use GParted to create a new partition:
Parition: /dev/sdb3
Filesystem: ext3
Mountpoint:
size: 25 GB
Used: 374.99MB
unused: 24.78 GB

But how can i use that parition? How can I auto-mount to as start copying files there?

Thank you.

First make a mount point, something in /media is "standard". I will use sdb3, but you can use what you wish.

```
sudo mkdir /media/sdb3
```

Mount :

```
mount /dev/sdb3 /media/sdb3
```

Set ownership and permissions with chown and chmod

```
sudo chown user.user /media/sdb3
sudo chmod 700 /media/sdb3
```

"user" = your log in name

To mount it at boot add this to fstab (edit fstab with gksu):

```
gksu gedit /etc/fstab
```

Add these lines (at the bottom is fine) :
```
# /dev/sdb3
/dev/sdb3  /media/sdb3  auto  defaults  0  2
```

:twisted:

---

### Post by VMC on 2008-06-30
FYI:
```
sudo kkdir /media/sdb3
```

should be :
```
sudo mkdir /media/sdb3
```

---

### Post by vikyrulz on 2008-06-30
hi... can anyone please tell me how this command works??? 

> # /dev/sdb3
/dev/sdb3  /media/sdb3  auto  defaults  0  2


I would like to know what each parameter does..

Thank you in advance!

---

### Post by russlar on 2008-06-30
> **vikyrulz said:**
> hi... can anyone please tell me how this command works??? 




I would like to know what each parameter does..

Thank you in advance!

THose are lines in /etc/fstab. 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

those are the column headers (taken from the first line in /etc/fstab)

---

### Post by yinglcs2 on 2008-07-02
Thank you for the help.

---

