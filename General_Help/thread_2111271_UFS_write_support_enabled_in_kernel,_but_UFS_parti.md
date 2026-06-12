---
title: "UFS write support enabled in kernel, but UFS partition mouted as read only"
date: 2013-02-01
forum: General Help
---

### Post by sguerrini97 on 2013-02-01
Hi. I've got a raw UFS2 partition image and I would like to write on it. On the web I've found that UFS2 write support in linux is dangerous/experimental, but I wanted to try anyway, so I recompiled my kernel from source and enabled UFS write support but the partition is still mounted as read-only. Why?

To mount I use this command:
```
sudo mount -t ufs -o ufstype=ufs2,rw ./image.img /mnt
```
Then I get
```
mount: warning: /mnt seems to be mounted read-only.
```
I think this mean that UFS write support was enabled correctly (because when it wasn't enabled mount gave me an error). However the partition is mounted as read only..

Thanks in advance.

---

### Post by sguerrini97 on 2013-02-02
bump, can it dipend from the image? Should I use an HDD?

---

### Post by rnerwein on 2013-02-02
> **sguerrini97 said:**
> bump, can it dipend from the image? Should I use an HDD?
hi
have a look at the man pages: man mount - and there mounting an ufs-filesystem (it's a never ending story). i had the same problem with the sun-ufs.
try a remount: mount -o rw ......
what does your system tells you if you try this.
cheers

---

### Post by sguerrini97 on 2013-02-02
> **rnerwein said:**
> hi
have a look at the man pages: man mount - and there mounting an ufs-filesystem (it's a never ending story). i had the same problem with the sun-ufs.
try a remount: mount -o rw ......
what does your system tells you if you try this.
cheers

Thank you a remount worked!
So this is what I have to do to mount the image as read-write:
```
sudo mount -t ufs -o ufstype=ufs2,rw ./image.img /mnt
sudo mount -o remount,rw /mnt
```
Really thank you again! Problem solved!

I don't know how to add "reputation", maybe I can't because I'm new :(

---

