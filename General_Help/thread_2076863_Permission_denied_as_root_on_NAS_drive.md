---
title: "Permission denied as root on NAS drive?"
date: 2012-10-27
forum: General Help
---

### Post by smaug42 on 2012-10-27
This is a bit frustrating and I'm not sure what I'm doing wrong here.

I've got a Verbatim 2TB NAS drive connected into my home network (NAS is formatted with ext2, and has Samba and NFS enabled).  Previously I've been using it with another Linux distro, and it's worked OK with Smaba and NFS. I've moved over to Kubuntu and am running into an annoying problem with existing files on the NAS.

The NAS is mounted like this in the fstab:
```
//10.0.0.6/media /media/NAS cifs credentials=/root/.smbcredentials,iocharset=utf8,gid=100,uid-1000,nounix,nobrl,file_mode=0777,dir_mode=0777 0 0

```

With that I can create files on the NAS, but I'm running into problems reading, copying or otherwise interacting with files already on the NAS.

For example, this file:
```
-rwxrwxrwx 0 root users 15975 Oct 13 12:34 accounts.xml*
```

Which should be wide open to the world cannot be accessed by my main user (who is a member of users) or by root.  If I try to view the file using sudo I get this back:

```
sudo less accounts.xml
accounts.xml: Permission denied
```

If I try to chmod or chown the file as root (using sudo) I get the same Permission denied error.

So my question to you experts is... where have I gone wrong? What needs to be solved so that I can copy this (and thousands of other files) off the NAS?  Is this something I can only do with NFS, and not with Samba?

---

