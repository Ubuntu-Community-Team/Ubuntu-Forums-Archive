---
title: "s flag on /etc/mtab permissions"
date: 2013-06-18
forum: General Help
---

### Post by mErchamion on 2013-06-18
hi everybody, I had a weird situation here. permissions on /etc/mtab got weird, they read:

# ls -al /etc/mtab
srwxrwxrw- someusernotroot someusernotroot  (somedate) (sometime) /etc/mtab

and this derived in the problem that I could not mount any partition on hda except root, home and others in fstab. df -h returned something the error:

df: cannot read table of mounted file systems: No such device or address

and when editing (as root) /etc/mtab with vim it read as a blank file, and [permission denied] was shown in the status bar. 

someusernotroot is a user I have set for sharing in my LAN, and automounts a samba share on other users home. the setup has been working for about a year wothout any problems. 

chmod and chown could be performed just fine on this /etc/mtab, but I found no way to remove the s flag, and the problem could not be solved that way.

Finaly I solved the problem removing the /etc/mtab and rebooting. a new /etc/mtab was created and everything works fine again.

So, the question is, What the hell has happened here? was my system intruded somehow or was it just a random system corruption ( my physical location has a awefull electric suply network which caused me HD corruptions before)? 

thank you all in advance.

---

