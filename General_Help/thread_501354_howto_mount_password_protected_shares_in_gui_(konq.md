---
title: "howto mount password protected shares in gui (konqueror) by clicking with the mouse"
date: 2007-07-15
forum: General Help
---

### Post by martini2 on 2007-07-15
Hi
I have the folowing lines in my fstab
```
//server/local  /mnt/server/local  cifs  user,noauto,atime,auto,rw,nodev,exec,nosuid  0  0

sshfs#martini2@server:/var/local  /mnt/server/local2  fuse  comment=sshfs,users,noauto,allow_other,reconnect,transform_symlinks  0  0

```
and can mount the shares after typing in the password in a terminal without problems but i want to mount/dismount them by clicking on a link in  my homefolder and being able to enter the password or even a username and a password. 
(like mountig other partitions: rightclick on the icon, mount, enter username&password, green triangle apears on the icon). Of course the system has to dismount them on reboot or shutdown.

There are a lot of postings here about automounting or automounting without passwords but none of them suits my needs. I will not put usernames and passwords in fstab or any other (credential)files. Any ideas how to solve this?

PS.  It is the same share as i have not decided what system to use, sshfs or cifs.

---

