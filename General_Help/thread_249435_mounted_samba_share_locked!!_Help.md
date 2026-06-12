---
title: "mounted samba share locked!! Help"
date: 2006-09-02
forum: General Help
---

### Post by ruppmeister on 2006-09-02
Ok heres my situation. I have tried all I can think of and everything on the forums here that I could find and still can not resolve this issue.

What I am trying to do is mount a samba file on my desktop for browsing purposes in apps. Well I have followed the guide on [http://www.ubuntuguide.org](http://www.ubuntuguide.org) to mount network folders on startup (13.16). When I follow these directions I get a folder on my desktop that has a lock on it. I have tried to change the permissions on it so that I can write to it using chmod -R 755 and chown commands and everytime I try this it gives me operation not permitted I also tryed it with sudo and same thing. What makes things even more frustrating is that I can go to Places->Network Servers-> and browse to the folder where I DO have permissions to R/W.

Here is my fstab file to see if I have something wrong.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.2.6/mnt    /home/ruppmeister/Desktop/Test smbfs  credentials=/root/.smbcredentials,dmask-777,fmask-777    0    0

---

### Post by kupajava on 2006-09-06
the umask and dmask commands need an equals sign not a dash

---

### Post by ruppmeister on 2006-09-06
Ok, Im not at home right now but will give it a try when I get home.

Thanks

---

