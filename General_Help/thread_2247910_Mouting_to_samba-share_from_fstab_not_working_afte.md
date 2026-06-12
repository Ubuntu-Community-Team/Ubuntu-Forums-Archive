---
title: "Mouting to samba-share from fstab not working after latest update"
date: 2014-10-11
forum: General Help
---

### Post by pacmyc1 on 2014-10-11
Hi.
Im running several PC's with Lubuntu 64-bit.
Until some time ago they were all mounting fine to my samba share (a NAS drive), but after 
kernel updates (I've been running apt-get upgrade and apt-get dist-upgrade) the share is no  more
beeing mounted on startup.

If I run sudo mount -a from terminal I get 
```
mount: //192.168.0.10/internal: can't read superblock
```

I can still connect from the PCManFM filemanager by entering smb://192.168.0.10/internal
but then I have to enter the login credentials after each reboot (One more issue here, the credentials are never saved nevertheless that I check 
the checkbox that I want to save them)

My fstab entry looks like this:
```
//192.168.0.10/internal /mnt/NAS cifs uid=****,rw,user=****,password=****,netbiosname=MyPC,port=139 0 0
```

---

### Post by AKZMonster on 2015-08-22
Unanswered... did you ever figure it out? I am also having issues

---

