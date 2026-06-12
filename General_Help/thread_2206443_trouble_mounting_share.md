---
title: "trouble mounting share"
date: 2014-02-19
forum: General Help
---

### Post by josiahrulez on 2014-02-19
Hey all, 

so im having trouble auto mounting a windows share at start up

i put the following into /etc/fstab
[FONT=Calibri][I]//servername/sharename /media/windowsshare cifscredentials=/home/ubuntuusername/.smbcredentials,iocharset=utf8,sec=ntlm 0 0 
[/I][/FONT]

It mounts ok, but only the root user can write to the folder?

how can i fix this?

---

### Post by TheFu on 2014-02-19
Have you set the user, uid, and gid option?
**man mount.cifs** for details.

---

