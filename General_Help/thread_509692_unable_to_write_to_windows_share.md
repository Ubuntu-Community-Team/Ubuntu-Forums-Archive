---
title: "unable to write to windows share"
date: 2007-07-25
forum: General Help
---

### Post by bowens44 on 2007-07-25
I am able to mount a windows share but I am unable to write to it without using 'sudo'.

I have the following entry in my fstab:

//192.168.5.100/linux_bkups /home/backups cifs nosuid,nodev,noexec,credentials=/etc/samba/auth.smb,uid=500,gid=500,file_mode=0664,dir_mode=0755 0 0

This mounts the share and I can read from it but can't write to it. I get permission denied.

in /etc/samba/auth.smb I have username  and password

What did I do wrong?

Thanks

---

### Post by ceege on 2008-03-05
I had this same issue and for me it was a matter of chown'ing the mounted directory.  

It was owned by root, so only root could write to it.

Hope that helps.

Chris

---

