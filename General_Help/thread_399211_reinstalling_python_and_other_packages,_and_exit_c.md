---
title: "reinstalling python and other packages, and exit code 127"
date: 2007-04-02
forum: General Help
---

### Post by fearpi on 2007-04-02
I really screwed up a lot of python related stuff on this machine and now I need to reinstall it. Important executables are gone, but Synaptics says all the packages are installed. When i try to remove python, it wants to remove practically every other package on my machine. So I try reinstallation instead - this gives an error for nearly every package I try:

E: /var/cache/apt/archives/python-gnome2_2.16.0-0ubuntu6_i386.deb: subprocess new pre-removal script returned error exit status 127

What does this even mean? I really need to just reinstall these packages.

---

### Post by zvacet on 2007-04-02
> /var/cache/apt/archives/python-gnome2_2.16.0-0ubuntu6_i386.deb
That tell you where is program downloaded.Even synaptic told you that program is installed mark it for reinstall and see what will be.

---

### Post by fearpi on 2007-04-02
I don't think you understand. I had it marked for reinstallation, and it gave me that error every time I tried to reinstall it.

Anyway, I resolved that one particular package, but now I'm working on update-manager which doesn't work.

```
brian@virgon:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
ImportError: No module named UpdateManager.UpdateManager
brian@virgon:~$ sudo apt-get install update-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4-minimal (2.4.4~c1-0ubuntu1) ...
Linking and byte-compiling packages for runtime python2.4...
python or pycentral not found in pycentral.rtinstall hook.
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I fix python2.4-minimal?

---

