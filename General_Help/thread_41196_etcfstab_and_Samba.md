---
title: "/etc/fstab and Samba"
date: 2005-06-12
forum: General Help
---

### Post by BerryB on 2005-06-12
Hello,

I'm trying to let Ubuntu auto-mount my smbshares. This is my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hdb1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# SMB shares
//BAKKER/Documenten /mnt/SmbWin/Doc     smbfs   defaults,user=Eigenaar,password=  0     0
//BAKKER/Overnet /mnt/SmbWin/Overnet    smbfs   defaults,user=Eigenaar,password=  0     0
```

But on startup it complains that it's unable to locate the tree or something... But when I type mount -a, it mounts the SMB shares. So what's te problem?

---

### Post by maher on 2005-06-12
what is the exact output?
- put the IP instead of the hostname, maybe it's something to do with the runlevels. 
try to use cifs to mount samba shares.

---

### Post by crane on 2005-06-12
I personally haven't mounted smb share with fstab (I use NFS)
But, wouldn't you need to supply a user name?
I take it the mounts are one a computer named BAKKER?
> 
//BAKKER/Documenten /mnt/SmbWin/Doc

Maybe you need to give a user name at the front,

//Eigenaar@BAKKER/Documenten /mnt/SmbWin/Doc smbfs   defaults password=***   0     0

Just a though.

Good Luck

---

### Post by RastaMahata on 2005-06-12
this isnt the place to ask questions...
admins, please move this.

---

### Post by Ainvar on 2005-06-12
How do you use cifs, I have not found a way to do that I understand.

---

### Post by maher on 2005-06-12
> //host_name_or_ip/distant_folder   /local_folder  cifs cifsexec,credentials=/etc/cifspw   0   0

you must create a file and name it whatever you like, i chose /etc/cifspw, inside you need to put something like:

> username=your_user_name
password=your_password

though I am sure your problem has something to do with runlevels

please, in the future post your questions in another forum.

---

