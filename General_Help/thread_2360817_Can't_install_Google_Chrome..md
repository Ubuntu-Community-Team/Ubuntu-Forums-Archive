---
title: "Can't install Google Chrome."
date: 2017-05-08
forum: General Help
---

### Post by Hewjr100 on 2017-05-08
Trying to install google chrome in ubuntu 17.04 and get the following:

```
henry@wyatt:~/Downloads$ sudo dpkg -i *.deb
Selecting previously unselected package google-chrome-stable.
(Reading database ... 206090 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (58.0.3029.96-1) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on gconf-service; however:
  Package gconf-service is not installed.
 google-chrome-stable depends on libgconf-2-4 (>= 2.31.1); however:
  Package libgconf-2-4 is not installed.
 google-chrome-stable depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not installed.
 google-chrome-stable depends on libappindicator1; however:
  Package libappindicator1 is not installed.

dpkg: error processing package google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3+17.04.20170406-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for man-db (2.7.6.1-2) ...
Errors were encountered while processing:
 google-chrome-stable
henry@wyatt:~/Downloads$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  google-chrome-stable
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 215 MB disk space will be freed.
Do you want to continue? [Y/n
```

Henrhy

---

### Post by again? on 2017-05-08
> google-chrome-stable depends on gconf-service; however:
  Package gconf-service is not installed.

Install gconf-service.

---

### Post by Hewjr100 on 2017-05-08
i tried.

```
henry@wyatt:~$ sudo apt install gconf-service
[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gconf-service is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gconf-service' has no installation candidate
henry@wyatt:~$
```

Henry

---

### Post by again? on 2017-05-08
Do you have the universe repo enabled?
```
apt policy gconf-service
```

```
$ apt policy gconf-service
gconf-service:
  Installed: 3.2.6-3ubuntu7
  Candidate: 3.2.6-3ubuntu7
  Version table:
 *** 3.2.6-3ubuntu7 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) zesty/**universe** amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Hewjr100 on 2017-05-08
Well can't say I do, but I just finished installing ubuntu 16.04.2 with google chrome installed.  Pretty fast eh.

Henry

---

### Post by again? on 2017-05-09
> **Hewjr100 said:**
> Well can't say I do, but I just finished installing ubuntu 16.04.2 with google chrome installed.  Pretty fast eh.

Henry
:p Doesn't take long.
I had to go out. Just got back.
 
FYI I prefer to use gdebi for installing debs as it will resolve dependencies.
dpkg doesn't automatically resolve dependencies.
It just leaves the installed package unconfigured where you have to run 'apt install -f' to install the dependencies and configure.
If a dependency isn't available it will prompt to remove the original deb install.
Can be confusing at times.
Looks like you're up and going anyway. ;)

If you don't know... the universe repo should have been enabled by default and can be checked by running.
```
software-properties-gtk
```

---

