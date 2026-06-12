---
title: "mount cdrom as user?"
date: 2005-07-03
forum: General Help
---

### Post by jkarpago on 2005-07-03
Hi:
When I try to mount my cdrom I allways have to do it as root or with the sudo command.

Is there a way that a simple user can access to cdrom with the command 

mount /dev/cdrom /media/cdrom0

?

Thanks so much

---

### Post by phen on 2005-07-03
you have to add an entry to the file /etc/fstab:

sudo gedit /etc/fstab

add the following line:

/dev/cdrom        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

Note the "user" tag in the options field. It says that every user is allowed to (u)mount! 

make backups of your files, because fstab is an important system file!

cheers,

kai

---

### Post by WMCoolmon on 2005-07-03
[QUOTE=jkarpago]Hi:
When I try to mount my cdrom I allways have to do it as root or with the sudo command.

Is there a way that a simple user can access to cdrom with the command 

mount /dev/cdrom /media/cdrom0

?

Thanks so much[/QUOTE]
 Ubuntu mounts CDs (for me) automatically.

IIRC, though, it'd be something like this:

mount /dev/cdrom /media/cdrom0 -o umask=022

---

### Post by jkarpago on 2005-07-04
Thanks so much for your help

---

