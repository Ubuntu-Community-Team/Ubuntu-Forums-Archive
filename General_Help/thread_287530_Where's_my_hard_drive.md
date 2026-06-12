---
title: "Where's my hard drive?"
date: 2006-10-28
forum: General Help
---

### Post by hucmoh on 2006-10-28
I cannot find any reference to my hard drive in my system:

harvey@ubuntu:~$ ls -l /dev | less
. . . .
crw-rw-rw- 1 root root      1,   7 2006-10-28 21:27 full
brw-rw---- 1 root cdrom     3,  64 2006-10-28 21:27 hdb
crw-rw---- 1 root root     10, 228 2006-10-28 21:27 hpet
. . . .

harvey@ubuntu:~$ sudo fdisk /dev/hda
Password:

Unable to open /dev/hda
harvey@ubuntu:~$

harvey@ubuntu:~$ sudo hdparm -tT /dev/hda
/dev/hda: No such file or directory
harvey@ubuntu:~$

I have a working system so I have a hard drive. Isn't the hard drive always /dev/hda? Why isn't it showing up in my system, and why are diagnostic commands not returning any info about the hard drive?

Thanks.  ~Harvey

---

### Post by NetworkGuy on 2006-10-28
Try df from a command prompt.  That may help guide you to your hard drive location

---

### Post by DaveBorealis on 2006-10-28
Or you could instead do 'sudo fdisk -l' (that's an ell) to see what all is on your system.

Dave

---

### Post by handy on 2006-10-28
You could have a look at your:

**gedit /etc/fstab** & see what your **/** drive is mounted as?

Or you could type:

**mount**

& get the full list.

---

### Post by taurus on 2006-10-28
Or maybe because you have a SATA drive and it's /dev/sda instead of /dev/hda!!!

---

### Post by handy on 2006-10-28
> **taurus said:**
> Or maybe because you have a SATA drive and it's /dev/sda instead of /dev/hda!!!

I thought that the fstab might be interesting?

---

### Post by taurus on 2006-10-28
> **handy said:**
> I thought that the fstab might be interesting?
Yes, either /etc/fstab or "df -h" will solve the whole problem...  ;)

---

### Post by handy on 2006-10-29
> **taurus said:**
> Yes, either /etc/fstab or "df -h" will solve the whole problem...  ;)

Hmmm... **df -h** is so much tidier than **mount**! :) 

I'll remember that.

---

### Post by taurus on 2006-10-29
> **handy said:**
> Hmmm... **df -h** is so much tidier than **mount**! :) 

I'll remember that.
It's a nice little command to check on your space!  ;)

---

