---
title: "chmod problem"
date: 2008-06-26
forum: General Help
---

### Post by fuatsungur on 2008-06-26
hi, before i've installed ubuntu 8.04, i had partitioned my harddisk to two disk. size of one of them is 88.0 GB, i can access it /media/disk/lost+found/ in terminal properly. But, i couldn't access it in File Browser by click on Media folder and click on "disk" and click on "lost+found" folder. But i got an error message :" permission denied". So, i decided to change chmod attribute of "lost+found" folder in terminal through change chmod of that folder as "777". Now i can access it in terminal, there is no problem, but i can't see any folder under the "/media/disk/" folder in File Browser. 

Do you have any advice to solve it?
Thans for responses.

---

### Post by fuatsungur on 2008-06-26
i forget to say, i could access this folder as root user in terminal. But, in GUI in File Browser i can't see "lost+found" folder in "media/disk/" folder.

---

### Post by Claus7 on 2008-06-26
Hello,

I would suggest you to do chmod in /media/disk and see what will happen.

Regards!

---

### Post by mcduck on 2008-06-26
You are not even supposed to be able to access or modify that directory as normal user. It's a system directory and belongs to root. I would recommend changing it's permissions back to original ones, as changing the ownership or permissions of system files/directories can cause seripus problems.

If the drive is internal one, and you want to be able to access it as normal user, you should change the mount options for the drive in /etc/fstab. If it's external drive you'd better to just create a directory into the drives root and then chown _that_ directory to your own user.

(lost+found is used by fsck as a place to store lost/corrupted files. You shouldn't put anything else there.)

---

