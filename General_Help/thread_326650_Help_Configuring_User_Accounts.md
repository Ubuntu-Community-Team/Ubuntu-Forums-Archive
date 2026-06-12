---
title: "Help Configuring User Accounts"
date: 2006-12-27
forum: General Help
---

### Post by dshack on 2006-12-27
I just installed Edgy on my Thinkpad T60 laptop.  My installation worked fine until I played around a little too much and corrupted my superuser account to the point that I cannot login.  So, I rebooted and added another account using the recovery mode and my root account.  This new account does not have superuser rights and I cannot access the "Users and Groups" tab because I don't have the privileges.  I need to have superuser rights on my new account.  Is this possible?  Is there any way to have a newly created user w/ superuser rights?  How do I do this using command line and/or my root account?  Thanks in advance!

---

### Post by taurus on 2006-12-27
Boot into recovery mode from GRUB menu and add that username to both groups **adm** (near the top) & **admin** (near the end of the file) in /etc/group...

```
nano -w /etc/group
```
Reboot and you are all set.

```
shutdown -r now
```

---

### Post by dshack on 2006-12-28
Thanks!

---

