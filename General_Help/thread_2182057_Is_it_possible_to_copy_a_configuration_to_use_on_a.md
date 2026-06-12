---
title: "Is it possible to copy a configuration to use on another server."
date: 2013-10-19
forum: General Help
---

### Post by bt1996 on 2013-10-19
Hello,

I am going to need a couple of essentially the same servers. After finishing 1 server already, I am wondering if it is possible to copy+ paste the disk to the new server? The 2 servers are exactly identical in terms of hard ware and software. Is there such a program that would do this for me? 

Thank you

---

### Post by drmrgd on 2013-10-20
One of the companies I work with deploy their analysis servers with the same exact software (all of the hardware is identical, which I think is what is necessary to make this work), by using an image made with Clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

The docs seem pretty good and might give you and idea about how to do it.  But essentially they have an image that they use to configure the RAID array and set up the entire OS and all of the analysis packages to make the server identical to the others.  Maybe this will put you on the path you want?

---

### Post by bt1996 on 2013-10-20
It could be! Thank you I will certainly test this out. :)

---

### Post by Habitual on 2013-10-20
tsk tsk.
dump of installed software>
 ```
dpkg --get-selections > /root/installed-software.log
```

use dump file on new host to install said software:
 ```
dpkg --set-selections < /root/onstalled-software.log
```

from [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)
which is referenced at [https://help.ubuntu.com/community/InstallingSoftware#Backup.2BAC8-Restore_installed_packages](https://help.ubuntu.com/community/InstallingSoftware#Backup.2BAC8-Restore_installed_packages)

---

### Post by drmrgd on 2013-10-21
> **Habitual said:**
> tsk tsk.
dump of installed software>
 ```
dpkg --get-selections > /root/installed-software.log
```

use dump file on new host to install said software:
 ```
dpkg --set-selections < /root/onstalled-software.log
```

from [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)
which is referenced at [https://help.ubuntu.com/community/InstallingSoftware#Backup.2BAC8-Restore_installed_packages](https://help.ubuntu.com/community/InstallingSoftware#Backup.2BAC8-Restore_installed_packages)

Yes, this is certainly a good way to capture all of the software you want to have installed on all servers.  But the disc clone method is very convenient if you don't want to have to deal with configuring all of it too.  After the vendor loads up the system with the disc image, they whole system is ready to go right out of the box and about the only thing that needs to be configured is the networking stuff.

---

