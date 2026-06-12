---
title: "[SOLVED] mount as normal user"
date: 2007-09-22
forum: General Help
---

### Post by jimmywu013 on 2007-09-22
Hi, 

Does anyone know how to mount filesystems with user permissions?  When I use mount, I have to use sudo, and the filesystem gets mounted as owner root, group root.

Specifically, I'm trying to mount a windows share with
mount -t cifs //windows-box/share /mount/point -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

Even though my mount point has my permissions, it goes to root after I mount the share there.
I've tried adding the mount to /etc/fstab/ and adding the user option, but I still can't mount without sudo, and I still end up with it mounted as root.

Thanks,

Jimmy

BTW -- FIrst Post!
--
Registered Linux User #454138

---

### Post by reckless2k2 on 2007-09-22
you are going to have to mount in fstab using something like this:

```
//windows-box/share /mount/point    cifs     theusername=username,thepassword=password,uid=theuser,gid=thegroup,dir_mode=0770,file_mode=0770    0    0
```

to "hide" the user/passwd combo use credentials if you are worried about it. i think you know what i mean. 

let me know if you got it.

0770 will mount it so only people in that user and group will be able to r/w.

---

### Post by jimmywu013 on 2007-09-22
Thanks reckless2k2!
The part I needed was the uid= and gid=, and that got the share to mount with my permissions.
BTW, I still usde -o guest instead of the username, password because the windows share is not password protected

Thanks again,

Jimmy

---

### Post by reckless2k2 on 2007-09-22
not a problem. glad to help.

---

