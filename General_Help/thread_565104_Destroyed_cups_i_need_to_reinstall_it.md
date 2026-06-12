---
title: "Destroyed cups i need to reinstall it"
date: 2007-10-01
forum: General Help
---

### Post by CameronCalver on 2007-10-01
Hello i was trying to set up network printing and i completly destroyed cups.
 I then replaced the ```
/etc/cups/cupsd.conf
``` with a working cups config from another working computer running ubuntu fiesty.
I no cannot go into system --- admin -- printers it says error the cups server could not be contacted how do i fix this?

---

### Post by gautada on 2007-10-01
Why not just delete the file and mark the "cupsys" package for reinstall?

---

### Post by CameronCalver on 2007-10-01
this is why
```
calver@ubuntu:~$ sudo aptitude reinstall cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libpq5 linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-386 mozilla-thunderbird update-manager-core 
The following packages have been kept back:
  app-install-data-commercial kdelibs-data libjasper-1.701-1 libkrb53 
  libqt3-mt libssl0.9.8 libwrap0 linux-libc-dev openssl rsync tar tcpd 
  update-manager vim vim-common vim-runtime vim-tiny 
The following packages will be REINSTALLED:
  cupsys 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cupsys (1.2.8-0ubuntu8) ...
chown: cannot access `/etc/cups/cupsd.conf': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys (1.2.8-0ubuntu8) ...
chown: cannot access `/etc/cups/cupsd.conf': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
calver@ubuntu:~$ 

```

---

### Post by bensode on 2007-10-02
sudo apt-get check        (dependency check)

sudo apt-get remove --purge cupsys                  (obliterate cupsys)

sudo apt-get install cupsys                             (install cupsys)

Try those in that order.  Please note that "remove --purge" will remove any related cupsys apps and config files that are not dependent on any other currently installed programs.

---

