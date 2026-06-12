---
title: "Skype"
date: 2014-08-31
forum: General Help
---

### Post by Chrisinthedark on 2014-08-31
Hi,
I have a problem. I can't install any program. Everytime it says:

```
skype:i386 :  Depends: libqt4-webkit:i386 (>= 4:4.6.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I have installed Skype 4 because I was forced to.

So, if I run sudo apt-get -f install

```

chris@chris-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libqt4-webkit:i386
The following NEW packages will be installed
  libqt4-webkit:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8,004 B of archives.
After this operation, 133 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libqt4-webkit
Install these packages without verification [y/N]? Y
Err http://gb.archive.ubuntu.com/ubuntu/ raring-updates/universe libqt4-webkit i386 4:4.8.4+dfsg-0ubuntu9.5
  404  Not Found [IP: 194.169.254.10 80]
Err http://security.ubuntu.com/ubuntu/ raring-security/universe libqt4-webkit i386 4:4.8.4+dfsg-0ubuntu9.5
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-webkit_4.8.4+dfsg-0ubuntu9.5_i386.deb  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Ok then... sudo apt-get --fix-missing

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 skype:i386 : Depends: libqt4-webkit:i386 (>= 4:4.6.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

Let's try to uninstall Skype:

sudo apt-get remove skype

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'skype' is not installed, so not removed. Did you mean 'skype:i386'?
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 skype:i386 : Depends: libqt4-webkit:i386 (>= 4:4.6.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Please help me!!! I'm going mad!

Thanks

---

### Post by ajgreeny on 2014-08-31
Get the skype.deb for ubuntu 12.04 direct from [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) ; just ignore the fact that it is supposedly for 12.04; it works fine.

This is a multiarch package and installed perfectly without problems on my 64bit Xubuntu 14.04 system; I have just installed it to make sure, and the dependency for that skype package is libqtwebkit4, which is installable and in the repos.

For some reason the repository version of skype appears to have dependencies which are not available.

EDIT:
I have only just noticed that you are using raring (13.04) according to the error message you showed us.  Raring is no longer supported, so you will have to update your system to 14.04 as you will probably have great difficulty using the End Of Life (EOL) repos for raring, and even if you managed to do so, it is, frankly, not worth the trouble.

---

