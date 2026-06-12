---
title: "samba mounting"
date: 2007-04-14
forum: General Help
---

### Post by reckless2k2 on 2007-04-14
I'm trying to mount a samba share in /etc/fstab with rw permissions to only a user or group. I'm not sure of the string. I don't want r/w permissions for anyone on the box. I only want certain a user or group to have rw permissions.

---

### Post by reckless2k2 on 2007-04-14
The current string I'm using is this:

//smb/share /mnt/point smbfs credentials=/file/location,uid=theuser,gid=thegrp 0 0

My issue is the I've got rw permissions without issue but now every other user that logs in can see the mapped drive. I want the drive to be only viewable by the rw user or grp and not viewable to anyone else. 

Right now, if i log onto another desktop, the share is viewable to me. I don't have rw permissions under another user but every user can see the drive and log into it even though they can't write to it. I've got rw on the user or grps I need but I need it cloaked to everyone else on login.

---

### Post by reckless2k2 on 2007-04-15
bump bump

---

### Post by reckless2k2 on 2007-04-17
For anyone interested, I used umask for the results I needed. With the syntax:

umask=006

Got me owner and group rw permissions while the rest couldn't even view the directory.

---

