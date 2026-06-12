---
title: "Help unlocking a partition."
date: 2008-03-16
forum: General Help
---

### Post by ErusGuleilmus on 2008-03-16
Hello,

I recently used GParted to make some free space on my hard drive into a storage partition that I would mount from Ubuntu. I was able to create the partition just fine, and Ubuntu mounted it as "Disk". The problem comes into play when I move files to and from the partition. It seems that I need to go into super user mode to do any thing read/write on it. This especially is irritating when I try to run virtual machines that I have stored on it. Is there any way to make it so that I do not have to go into super user when doing anything read/write related on that partition?

Thanks!

-Erus

---

### Post by logos34 on 2008-03-16
You need to change ownership and add to fstab:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by ErusGuleilmus on 2008-03-16
Worked perfectly.... thank you so much!

---

