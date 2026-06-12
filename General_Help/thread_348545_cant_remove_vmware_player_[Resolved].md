---
title: "cant remove vmware player [Resolved]"
date: 2007-01-28
forum: General Help
---

### Post by CameronCalver on 2007-01-28
Hello i installed vmware player to have a look at it but then i realised that i needed vmware server so i downloaded it and i cant remove vmware player i get this error
```
calver@ubuntu:~$ sudo apt-get remove vmware-player
]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
calver@ubuntu:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125279 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
calver@ubuntu:~$ 


```
does anyone no the solution to this problem

---

### Post by aysiu on 2007-01-28
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? *Is* another process using it? Synaptic? Adept? Add/Remove Programs?

---

### Post by CameronCalver on 2007-01-28
no im positive is there a way to reinstall dpkg

---

### Post by CameronCalver on 2007-01-28
Just a thing  i made sure nothing was open and did it again and this is what i got
```
calver@ubuntu:~$ sudo apt-get remove vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125279 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
calver@ubuntu:~$ 

```

---

### Post by aysiu on 2007-01-28
Check out [this thread](http://www.ubuntuforums.org/showthread.php?t=315493).

It has several solutions to try--some appear to work for people; others don't. They're worth a try, though.

---

### Post by CameronCalver on 2007-01-29
Thanks heaps aysiu for your help worked fine

---

