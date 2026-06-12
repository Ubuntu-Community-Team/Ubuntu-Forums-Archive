---
title: "How to mount the hard-drive with specific rights and share it on local network?"
date: 2014-08-22
forum: General Help
---

### Post by ppn029012 on 2014-08-22
I have create a samba server on Ubuntu 14.04 and sharing the stuffs in /home/user/Videos/.. smoothly. 

I have the HDD disk which contains a lot of resource I have to access. I mounted it in Files by clicking the Devices icons, and right click the folder I want to access to share it just as what I have done in /home/. 

But it seems the Samba service has not any permission to read and write these shared folders. And I can't change the permission of folders in the mounted disk.

I'm new to the mounting stuff, and don't know how to deal with it. How to mount it with special rights or how to grant a super privilege to Samba?


Thanks,
Yunong

---

### Post by TheFu on 2014-08-22
Which file system?  NTFS is different than UNIX-based file systems.

---

### Post by ppn029012 on 2014-08-23
I solved the problem by logging Samba folder with a specific account(which has the right permission for the file).

---

