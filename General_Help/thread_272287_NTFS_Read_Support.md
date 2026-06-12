---
title: "NTFS Read Support"
date: 2006-10-06
forum: General Help
---

### Post by bparham on 2006-10-06
I'm to set up my system to be able to read my Windows drive, however I'm getting the following error as seen in the attachment. I'm not sure where to go from here. 

Thanks!

---

### Post by jalm111 on 2006-10-06
What are you using to mount the ntfs volume? Can you show us your /etx/fstab file as well as output of df and fdisk -l (you gotta sudo to run the fdisk)?

Here's a working ntfs entry for the /etc/fstab file:
/dev/hdb1       /mnt/ntfs2      ntfs    nls=utf8,umask=0222     0       0

---

### Post by towsonu2003 on 2006-10-06
> **jalm111 said:**
> /etx/fstab

s/he means /etc/fstab

---

### Post by aysiu on 2006-10-06
Just follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

