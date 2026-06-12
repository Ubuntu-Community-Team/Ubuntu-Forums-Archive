---
title: "liblaunchpad-integration0 error in apt"
date: 2008-07-01
forum: General Help
---

### Post by eljaco on 2008-07-01
Hi, I have a problem when I upgrade and remove any package via apt:

```
~$ sudo apt-get upgrade
sudo: unable to resolve host Mickey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libdeskbar-tracker
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
40 not fully installed or removed.
Need to get 0B/22.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 
dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.
317170 files and directories currently installed.)
Preparing to replace libdeskbar-tracker 0.6.6-0ubuntu3 (using .../libdeskbar-tracker_0.6.6-0ubuntu3.8.04.1_all.deb) ...
WARNING: /usr/share/python-support/libdeskbar-tracker.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/libdeskbar-tracker.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.6-0ubuntu3.8.04.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/libdeskbar-tracker.dirs does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libdeskbar-tracker_0.6.6-0ubuntu3.8.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jaco@Mickey:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host Mickey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libdeskbar-tracker
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
40 not fully installed or removed.
Need to get 0B/22.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
jaco@Mickey:~$ sudo apt-get remove ekiga 
sudo: unable to resolve host Mickey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ekiga
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
40 not fully installed or removed.
Need to get 0B/22.5kB of archives.
After this operation, 15.0MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 
dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.
317168 files and directories currently installed.)
Removing ekiga ...
(Reading database ... 
dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.
316940 files and directories currently installed.)
Preparing to replace libdeskbar-tracker 0.6.6-0ubuntu3 (using .../libdeskbar-tracker_0.6.6-0ubuntu3_all.deb) ...
WARNING: /usr/share/python-support/libdeskbar-tracker.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/libdeskbar-tracker.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.6-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/libdeskbar-tracker.dirs does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libdeskbar-tracker_0.6.6-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jaco@Mickey:~$ 

```

The recurring problem I see is this:

```
dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.
```

But when I went to look for the package in [http://packages.ubuntu.com/hardy/liblaunchpad-integration0](http://packages.ubuntu.com/hardy/liblaunchpad-integration0) I get an error saying that package does not exist so I can't re/install it.

Thanks in advanced!

---

