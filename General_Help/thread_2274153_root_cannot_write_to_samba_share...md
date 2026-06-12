---
title: "root cannot write to samba share.. ?"
date: 2015-04-18
forum: General Help
---

### Post by mahela007 on 2015-04-18
(I'm running samba on a raspberry pi)
I've mounted a windows share using samba using the following entry in fstab. 
```
//192.168.1.70/H/windowsShare /media/mountPoint  cifs  credentials=/home/user/credentials/smbCred,iocharset=utf8,sec=ntlm  0  0
```

After mounting, the owner and group are both root and read, write and execute are enabled for root. 
However, even as root, I can't write to or make folders in the mounted directory. Why is this? 
(Before mounting, the owner of the /media/mountPoint directory is not root.. it's user. I don't know if that's significant)

---

### Post by nerdtron on 2015-04-18
Are you sure you enabled read/write for  a user on the windows share? Try to set the permission to read/write to everyone. It is still secure since you still need to set the user/password when mounting the share.

---

### Post by mahela007 on 2015-04-18
Thanks...that worked. I suppose I forgot to check the windows side of things

---

