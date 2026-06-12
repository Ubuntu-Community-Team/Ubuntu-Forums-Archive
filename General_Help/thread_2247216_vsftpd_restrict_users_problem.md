---
title: "vsftpd restrict users problem"
date: 2014-10-06
forum: General Help
---

### Post by Drenriza on 2014-10-06
Hi all.
Hope someone can help me with this pesky problem.

I have a debian 7.4.0 server installed, and on this i installed vsftpd.
I want to restrict my ftp users to _ONLY_ their home directory.

First i tried
```

chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list

```
Could not login, i read that this was duo to a security update.
So i remove the root executable bit chmod a-w /home/user. Still could not login.

So i tried
```

chroot_local_user=YES
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list

```
Can login, but i can browse the entire system from my ftp service.

the log /var/log/vsftpd.log does NOT tell me much, execpt
[user] OK LOGIN: Client 
And this does not matter if the login is a sucess or fails.

I dont get it, from what i can read chroot_local_user=YES should lock users to their home directory. But than i cant login.
chroot_list_enable=YES should restrict users on a list to their home directory, but can browse everything.

Its probably right infront of ME, but what am i missing in this?

Thanks on advance.
Kind regards.

---

