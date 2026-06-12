---
title: "Samba access to debian box from Ubuntu"
date: 2005-03-20
forum: General Help
---

### Post by motiv8d on 2005-03-20
I have a samba server on a debian testing box. A windows machine can access it with full write access without any problems (the windows login is a different from the share login, the ubuntu login is the same username but different password). My ubuntu machine has it setup in fstab, as for some reason I cannot get the networking program within ubuntu to connect. From fstab it is then available but only as read only (except when I access it from a root terminal). The same user and password is used from both ubuntu and windows.
Also the ubuntu machine can access a share on the windows machine. It is accessed from fstab exactly the same way as the non working debian samba share.
I do not know if the problem is with the debian samba server or with the ubuntu samba client, but it seems like the problem is on the ubuntu end.
Does anyone have any ideas of what the problem is or what I can try?

fstab is below (254 is debian machine and 121 windows xp):
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs defaults        0       1
/dev/hda8       /boot           reiserfs defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda5	/mnt/images	vfat	defaults	0	0
/dev/hda1	/mnt/xppro	ntfs	defaults	0	0
//10.10.10.254/fullshare /mnt/chewy-fullshare smbfs credentials=/home/jesse/.smbcredentials.chewy-fullshare,dmask=777,fmask=777 0 0
//10.10.10.121/f /mnt/yoda-f smbfs credentials=/home/jesse/.smbcredentials.yoda-motiv8d,dmask=777,fmask=777 0 0

Thanks

---

### Post by ubuntu_demon on 2005-03-22
I had a lot of problems with samba in warty. In hoary it's a bit better.

---

