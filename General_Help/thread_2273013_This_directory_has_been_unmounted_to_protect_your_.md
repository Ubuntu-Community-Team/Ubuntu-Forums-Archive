---
title: "This directory has been unmounted to protect your data"
date: 2015-04-10
forum: General Help
---

### Post by sirio81 on 2015-04-10
Hi, I'm trying to help a firend fixing his ubuntu installation.
His running 14.04.
Ubuntu starts but doesn't mount user's home directory.
I find a readme with
'THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA'.
Running ecryptfs-mount-private I'm able to mount the user home but I need this to happen automatically.
It stopped working after an update (no release change).

Note: even if the home is mounted, lightdm is unable to open the user session.

Thank you.

---

### Post by dino99 on 2015-04-10
might be related to ecryptfs, but i've no clue about it, sorry; maybe google around 'ubuntu+ecryptfs'

cat /etc/fstab may help to identify wrong parameter too when comparing with 'sudo blkid'

---

### Post by grahammechanical on 2015-04-10
Is login set to automatic without the need to enter a password?

I know nothing about encrypted home folders but it seems logical that a password would be required to give access to an encrypted home folder and that would normally happen when we login at the lightdm login screen. Again, I do not know for sure, but it seems logical to think that if the login was automatic then we might get to a desktop but without access to an encrypted home folder because it has not been unlocked.

Regards.

---

### Post by oldos2er on 2015-04-10
Moved to General Help.

---

### Post by awr on 2015-04-11
Sounds like you need to add the /home mount point in your /etc/fstab file.  The rest 'usually' happens automatically.

---

