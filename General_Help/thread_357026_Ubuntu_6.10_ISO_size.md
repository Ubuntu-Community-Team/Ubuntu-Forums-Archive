---
title: "Ubuntu 6.10 ISO size?"
date: 2007-02-09
forum: General Help
---

### Post by gavkearney on 2007-02-09
I have just downloaded the ISO for version 6.10, and I'm wondering if anybody knows the size the file should be? It says in the download window that it should be about 690 Mgs, but I have downloaded twice now, and it is only 590Mgs. I haven't tried installing yet, I just wanted to check the size. Anybody know?


Thanks.

---

### Post by sdide on 2007-02-09
Check the md5sum, its a better check than filesize.

do a 

```
md5sum <your_iso_file>.iso
```

and compare the result to the checksum given by the site where you download it.

example. I downloaded ubuntu-6.10-desktop-i386.iso from 
[http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/edgy/](http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/edgy/)

```
$ md5sum ubuntu-6.10-desktop-i386.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
$ 

```
and from the [http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/edgy/MD5SUMS](http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/edgy/MD5SUMS)
I get the line:
```
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
```

which fairly surely guaranties that the file is ok.

---

### Post by sdide on 2007-02-09
and about the filesize - 

```
$ ls -l ubuntu-6.10-desktop-i386.iso 
-rw-r--r-- 1 sdide sdide 732293120 2006-11-10 13:27 ubuntu-6.10-desktop-i386.iso
$ 
```

---

### Post by gavkearney on 2007-02-09
Cool, thanks a million. I'll check the checksum as soon as i get home. You're right, I'm sure that's definitely the best way to ensure the integrity of the ISO. Thanks.

---

