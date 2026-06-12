---
title: "can't mount iso image"
date: 2005-11-01
forum: General Help
---

### Post by kakashi on 2005-11-01
i created an iso images with this command 

> mkisofs -f -J -r -o ubuntu-dvd-0.iso ubuntu-dvd/ubuntu0

now when i try to mount them  this happens

> root@ubuntu:/store# sudo mount -t iso9660 -o loop /home/m/ubuntu-dvd-2.iso  /repos/dvd3/

mount: Not a directory


could somebody tell me what to do.

---

### Post by felix_stegerman on 2005-11-01
Did you create the /repos/dvd3/ directory ?
# sudo mkdir -p /repos/dvd3/


Felix

---

### Post by kakashi on 2005-11-01
ofcourse 
i made the directory. 
i am not that big a noob .
just a bit smaller:D

---

### Post by stoeptegel on 2005-11-01
My first thought: perhaps loop or mount only takes it when the directory is in /media?

---

### Post by felix_stegerman on 2005-11-01
Googling reveals that it might be a problem w/ the iso's directory structure.
What kernel do you use?

And how big is the original dir? and the iso? and what does "file <isofile>" say?


Felix

---

