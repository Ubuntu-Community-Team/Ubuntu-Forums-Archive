---
title: "SAMBA Permission"
date: 2013-04-11
forum: General Help
---

### Post by streat on 2013-04-11
I have created SAMBA users that sucessfully connect to the SAMBA shared folder but I cannot seem to grant read and write access to all users who can access the folder. Ideally I would like to remove all permissions from these folders as SAMBA users are the only ones who can mount the folders in the first place.
Thank you!

---

### Post by streat on 2013-04-11
Using 12.04 with desktop GUI

---

### Post by Morbius1 on 2013-04-11
It really depends on what you mean by read and write ( copy from and add to the share, edit the files within that share, or all of the above ) but we need to know the permissions of the folder you are sharing:
```
ls -dl /path/to/shared/folder
```
Remember that Samba controls who can access the share but Linux permissions controls what they can do when they get in.

---

### Post by streat on 2013-04-11
I would like all users to have read, write, and execute permissions

Echo:
drwxrwx--- 2 nobody nogroup 4096 Apr 11 10:33 /home/GREYHOLELZ/Books

---

### Post by streat on 2013-04-11
Solved my own problem haha, created a user group and gave the group access! Thanks for your help!

---

