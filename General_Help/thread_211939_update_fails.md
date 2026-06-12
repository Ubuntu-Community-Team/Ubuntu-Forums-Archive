---
title: "update fails"
date: 2006-07-09
forum: General Help
---

### Post by slimdog360 on 2006-07-09
I just installed a fresh copy of Dapper on my laptop and it tells me that it has updates available. Now I get this message when I try to update.
```
nick@nick-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  cupsys cupsys-bsd cupsys-client libcupsimage2 libcupsys2 libgnomecups1.0-1
  pmount
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2566kB of archives.
After unpacking 115kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://au.archive.ubuntu.com dapper-updates/main libcupsys2 1.2.1-0ubuntu1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main libcupsimage2 1.2.1-0ubuntu1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main cupsys 1.2.1-0ubuntu1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main cupsys-bsd 1.2.1-0ubuntu1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main cupsys-client 1.2.1-0ubuntu1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main libgnomecups1.0-1 0.2.2-1ubuntu5.1
  404 Not Found
Err http://au.archive.ubuntu.com dapper-updates/main pmount 0.9.11-1ubuntu1
  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
nick@nick-laptop:~$

```
I assume the 404 error means that the files have been moved, if so how can I fix this.
thanks

---

### Post by woedend on 2006-07-09
good question...
does this occur even after doing 
sudo apt-get update
first?  If so, what you can do it edit your /etc/apt/sources.list file and try removing the au. from those repos, so that it reads
deb [http://archive.ubuntu.com/](http://archive.ubuntu.com/)....
instead and doing another apt-get update.  LEt me know if that does it for you.

---

### Post by slimdog360 on 2006-07-09
success, thank you

---

