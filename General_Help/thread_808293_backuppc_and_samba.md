---
title: "backuppc and samba"
date: 2008-05-26
forum: General Help
---

### Post by Marco_Polo on 2008-05-26
I'm trying to backup using backuppc and would like for the backups to be stored directly onto a samba share.  I mount the samba share with the following fstab entry:

//EDmini.local/ED_mini /media/EDmini cifs username=backuppc,password=backuppc,rw,noexec  0 0

The command:
sudo mount /media/EDmini 

mounts the share.  My trouble, though is that only root can write to this directory.  It has permissions:

drwxrwxrwx 5 root 0 2008-05-26 09:36 /media/EDmini/

I get the following when I try to write:

touch /media/EDmini/tmp.blank
touch: cannot touch `/media/EDmini/tmp.blank': Permission denied

Anyone know how I can mount the share so my backup user "backuppc" can write to it?

---

