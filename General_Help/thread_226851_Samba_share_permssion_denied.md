---
title: "Samba share permssion denied"
date: 2006-07-31
forum: General Help
---

### Post by jonowoolley on 2006-07-31
I have samba set up on two machines running kubuntu dapper. One of them has a sucessful samba share and the other one is advertised to the network but will not let anyone acess it. In /var/log/samba/log.[host] on the non-working machine I get:

'/home/zeus/Desktop/storage/shared/' does not exist or permission denied when connecting to [SHARED] Error was Permission Denied.

The share config from smb.conf is:
path = /home/zeus/Desktop/storage/shared/
guest ok = yes
case sensitive = no
msdfs proxy = no

The share is a dir in an NTFS partition mounted writable using ntfs-3g. /etc/fstab has
/dev/hda5 /home/zeus/Desktop/storage ntfs-3g silent,umask=0,locale=en_NZ.utf8 0 0

Consequetially, the dir to be shared is owned by root. ls -la /home/zeus/Desktop/storage/ gives:
drwxrwxrwx 1 root root 4096 2006-07-16 21:33 shared

All these permissions are the same on the machine that works, which is also sharing a dir on a ntfs-3g mounted partition with the exact same settings (but at a different mount point).

I also checked if there was some part of samba not installed, but all the packages shown by adept as installed relating to samba or smb are also identical.

Does anyone have any idea what could be creating this problem? I have removed all iptables rules and still get the same result.

Thanks, Jono

---

### Post by jonowoolley on 2006-08-09
Turns out it was simply the share location. I tried mounting the ntfs partition at /home/[username]/storage instead of /home/[username]/Desktop/storage and modified smb.conf accordingly. Tada! It just worked. If anyone knows why Samba won't share stuff on the desktop I'd be interested to know. Is there some security reason?

Jono

---

