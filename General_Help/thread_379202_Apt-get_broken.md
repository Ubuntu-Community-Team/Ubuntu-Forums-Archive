---
title: "Apt-get broken"
date: 2007-03-08
forum: General Help
---

### Post by timbounceback on 2007-03-08
Apt-get is broken. When I try, for example, to install the package "kiba-dock", (which seems to be causing the problem) I get

tim@tim-laptop:~$ sudo apt-get install kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-core
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  kiba-dock
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 328kB of additional disk space will be used.
(Reading database ... 160766 files and directories currently installed.)
Unpacking kiba-dock (from .../kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/bin/populate-dock.sh', which is also in package kiba
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tim@tim-laptop:~$ 

This also doesn't allow me to install anything else  - 

tim@tim-laptop:~$ sudo apt-get install scribus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gset-kiba: Depends: kiba-dock but it is not going to be installed
  kiba-plugins: Depends: kiba-dock but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So, I ran "sudo rm -f /usr/bin/populate-dock.sh". This returns the same error. So, I run 'sudo apt-get -f install' like it suggests but..

tim@tim-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-core
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kiba-dock
The following NEW packages will be installed:
  kiba-dock
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 328kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160766 files and directories currently installed.)
Unpacking kiba-dock (from .../kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/bin/populate-dock.sh', which is also in package kiba
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help?

---

### Post by sbassett on 2007-03-08
OOOF, well removing the single file isn't the best course of action. Apt will go by what the file provides from the package itself, not from the filesystem contents. Try :

```

sudo apt-get clean
sudo apt-get -f install

```

---

### Post by timbounceback on 2007-03-08
Sorry for not replying sooner, but it doesn't work.

tim@tim-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-core
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kiba-dock
The following NEW packages will be installed:
  kiba-dock
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 83.9kB of archives.
After unpacking 328kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn kiba-dock 0.1.1+svn20070225~3v1ubuntu0 [83.9kB]
Fetched 83.9kB in 1s (71.8kB/s)   
(Reading database ... 160766 files and directories currently installed.)
Unpacking kiba-dock (from .../kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/bin/populate-dock.sh', which is also in package kiba
Errors were encountered while processing:
 /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kateikyoushi on 2007-03-08
Try to remove them.

```
sudo aptitude remove kiba-dock
sudo aptitude remove kiba
```

---

### Post by timbounceback on 2007-03-08
Thanks, with a bit of messing around with the dependencies I fixed it.

---

### Post by timbounceback on 2007-03-08
Oops, looks like I didn't look at it enough..

tim@tim-laptop:~$ sudo apt-get install scribus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gset-kiba: Depends: kiba-dock but it is not going to be installed
  kiba-plugins: Depends: kiba-dock but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tim@tim-laptop:~$ 

so i run -f install

tim@tim-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kiba-dock
The following NEW packages will be installed:
  kiba-dock
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 328kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160658 files and directories currently installed.)
Unpacking kiba-dock (from .../kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/bin/populate-dock.sh', which is also in package kiba
Errors were encountered while processing:
 /var/cache/apt/archives/kiba-dock_0.1.1+svn20070225~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

