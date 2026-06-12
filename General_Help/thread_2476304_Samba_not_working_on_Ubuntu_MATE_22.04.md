---
title: "Samba not working on Ubuntu MATE 22.04"
date: 2022-06-22
forum: General Help
---

### Post by MZ250Supa5 on 2022-06-22
I've recently upgraded to Ubuntu MATE 22.04 and as per usual wanted to set up samba share so I installed samba in the usual manner and also caja-share. Usually this 'just works' once I've rebooted,  instead I'm now getting 'net user share' returned error 255 when I try to set up a folder share.

I've tried some of the solutions I've found online, but none has worked. Anyone got any ideas?

---

### Post by yancek on 2022-06-22
You might indicate exactly what you have tried so that people don't suggest what you have already done.  Have you tried the suggestions at the link below?

[https://fostips.com/share-folder-ubuntu-21-04-fix-net-share-error-255/](https://fostips.com/share-folder-ubuntu-21-04-fix-net-share-error-255/)

---

### Post by Morbius1 on 2022-06-22
caja-share is broke. Here's a bug report for it: [https://bugs.launchpad.net/ubuntu/+source/caja-extensions/+bug/1972057](https://bugs.launchpad.net/ubuntu/+source/caja-extensions/+bug/1972057)

But wait, there's another problem.

The whole purpose of a samba usershare ( caja-share ) is for an ordinary user to share a folder he owns. That usually implies a folder in his home directory. Unless you make a share accessible only to you it won't work even if caja-share did still work because Ubuntu changed the default folder permissions of a user's home directory to username:username 0750.

Only you "username" can access the subfolders either locally or as a smb client.

My advice is to go old school and create your share definition in smb.conf directly. Example:

To share my Public folder I would edit /etc/samba/smb.conf and at the bottom of the file add a share definition that looks like this:

```
[Public]
path = /home/morbius/Public
read only = no
guest ok = yes
force user = morbius

```

Then restart smbd :
```
sudo service smbd restart
```

It will take years for a fix to show up in the repositories and by then there will be 16 other mate / gvfs / gnome bugs so beat the rush and use samba directly.

---

### Post by #&amp;thj^% on 2022-06-22
> **Morbius1 said:**
> 
My advice is to go old school and create your share definition in smb.conf directly. Example:

_by then there will be 16 other mate / gvfs / gnome bugs so beat the rush and use samba directly_.

:lolflag: Truer words have not yet been spoken

---

