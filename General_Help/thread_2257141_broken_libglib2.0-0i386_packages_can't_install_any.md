---
title: "broken libglib2.0-0:i386 packages can't install anything!"
date: 2014-12-17
forum: General Help
---

### Post by Smiff2 on 2014-12-17
hi this has been broken a while just became a problem though as i need to install something!

libglib2.0-0:i386 2.32.3-0ubuntu1 cannot be configured because libglib2.0-0:amd64 is in a different version (2.32.4-0ubuntu1)

> 

****@****-GA-MA69VM-S2 ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libindicate-qt1 libftgl2 libgomp1:i386 libprojectm2 libcroco3:i386 libechonest1.2
  libgettextpo0:i386 libqxt-core0 libqxt-gui0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglib2.0-0:i386
The following packages will be upgraded:
  libglib2.0-0:i386
1 to upgrade, 0 to newly install, 0 to remove and 578 not to upgrade.
5 not fully installed or removed.
Need to get 0 B/1,190 kB of archives.
After this operation, 11.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing libglib2.0-0:i386 (--configure):
 libglib2.0-0:i386 2.32.3-0ubuntu1 cannot be configured because libglib2.0-0:amd64 is in a different version (2.32.4-0ubuntu1)
dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.32.4-0ubuntu1 cannot be configured because libglib2.0-0:i386 is in a different version (2.32.3-0ubuntu1)
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.32.4-0ubuntu1); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:No apport report written because the error message indicates it's a follow-up error from a previous failure.


 firefox depends on libglib2.0-0 (>= 2.31.8); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:No apport report written because the error message indicates it's a follow-up error from a previous failure.


 flashplugin-installer depends on libglib2.0-0; however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 libglib2.0-0:i386
 libglib2.0-0
 libglib2.0-bin
 firefox
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)






looks like mismatch between 32bit and 64bit versions?

> sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.4-0ubuntu1) but 2.32.3-0ubuntu1 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.32.3-0ubuntu1) but 2.32.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.




any help appreciated! I am on precise. sources look ok?

> deb [http://mint.mirror.root.lu/packages/](http://mint.mirror.root.lu/packages/) maya main upstream import universedeb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise partner
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free


# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games
## Depôt MultiSystem
#deb [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all main
#deb [http://ppa.launchpad.net/b-eltzner/qpdfview/ubuntu](http://ppa.launchpad.net/b-eltzner/qpdfview/ubuntu) precise main
#deb-src [http://ppa.launchpad.net/b-eltzner/qpdfview/ubuntu](http://ppa.launchpad.net/b-eltzner/qpdfview/ubuntu) precise main

---

### Post by schragge on 2014-12-17
Yes, sources look OK. The problem is there's version mismatch between 32-bit and 64-bit versions of libglib2.0-0 installed on your system. Let's try to figure out *why* do you need the 32-bit version of libglib and if you need it at all. Please post the output of
```

apt-cache rdepends --installed libglib2.0-0:i386

```

---

### Post by Smiff2 on 2014-12-18
thanks,

> libglib2.0-0:i386Reverse Depends:
  gvfs-daemons
  gvfs
  wine1.4-i386:i386
  libgstreamer-plugins-base0.10-0:i386
  libcroco3:i386
  shared-mime-info
  libglib2.0-bin
  libglib2.0-bin
  libglib2.0-0
  libglib2.0-0
  gvfs-daemons
  gvfs
  glib-networking
  dconf-gsettings-backend
  wine1.4-i386:i386
  libgstreamer0.10-0:i386
  libgstreamer-plugins-base0.10-0:i386
  libglib2.0-0
  libglib2.0-0
  libgettextpo0:i386
  libcroco3:i386
  shared-mime-info
  libglib2.0-bin
  libglib2.0-bin
  gvfs-daemons
  gvfs
  glib-networking
  dconf-gsettings-backend




---

### Post by schragge on 2014-12-18
It seems wine1.4-i386 is the only installed non-library 32-bit package that depends on libglib2.0-0. If you don't use any 32-bit Windows programs then you can remove it and its dependencies:
```

sudo dpkg --remove wine1.4-i386
sudo apt-get autoremove

```

---

### Post by Impavidus on 2014-12-18
In any case nothing critical depends on the 32 bits libglib2.0-0 package. You should be able to uninstall it and reinstall it later.

All critical things on a 64 bit system depend on the 64 bit version of the library.


By the way, I don't fully agree with the "just became a problem". You have over 500 upgrades waiting. There will be some important security updates amongst those.

---

### Post by Smiff2 on 2014-12-18
> **schragge said:**
> It seems wine1.4-i386 is the only installed non-library 32-bit package that depends on libglib2.0-0. If you don't use any 32-bit Windows programs then you can remove it and its dependencies:
```

sudo dpkg --remove wine1.4-i386
sudo apt-get autoremove

```

thanks ah not sure how to do this?


> ****@****-GA-MA69VM-S2 ~ $ sudo dpkg --remove wine1.4-i386
[sudo] password for ****: 
dpkg: warning: there's no installed package matching wine1.4-i386
****@****-GA-MA69VM-S2 ~ $ sudo dpkg --remove wine1.4-i386:i386
dpkg: dependency problems prevent removal of wine1.4-i386:i386:
 wine1.4 depends on wine1.4-i386 (= 1.4-0ubuntu4.1); however:
  Package wine1.4-i386 is not installed.
  Package wine1.4-i386:i386 is to be removed.
dpkg: error processing wine1.4-i386:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 wine1.4-i386:i386




[COLOR=#DD4814][COLOR=#000000][Impavidus]("http://ubuntuforums.org/member.php?u=1417721"), [/COLOR][/COLOR]yes you are right it needs updating, i was planning to fully reinstall with 14.04, but that is on hold as i don't have time right now so would prefer to fix old system if possible. many thanks.

---

### Post by schragge on 2014-12-18
Then do it like this (you can reinstall *wine* later, after you're done with updates):
```

sudo apt-get remove wine1.4
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Smiff2 on 2014-12-18
not having much luck here! going round in circles :/

> ****@****-GA-MA69VM-S2 ~ $ sudo apt-get remove wine1.4[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.4-0ubuntu1) but 2.32.3-0ubuntu1 is to be installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.32.3-0ubuntu1) but 2.32.4-0ubuntu1 is to be installed
 wine1.4-common : Depends: wine1.4 (= 1.4-0ubuntu4.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
****@****-GA-MA69VM-S2 ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.4-0ubuntu1) but 2.32.3-0ubuntu1 is installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.32.3-0ubuntu1) but 2.32.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.


not sure if this was a good idea


> 
****@****-GA-MA69VM-S2 ~ $ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0:i386
The following packages will be REMOVED
  libcroco3:i386 libechonest1.2 libftgl2 libgettextpo0:i386 libgomp1:i386 libindicate-qt1 libprojectm2
  libqxt-core0 libqxt-gui0 libunistring0:i386
The following packages will be upgraded:
  libglib2.0-0:i386
1 to upgrade, 0 to newly install, 10 to remove and 577 not to upgrade.
5 not fully installed or removed.
Need to get 0 B/1,190 kB of archives.
After this operation, 5,395 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 156432 files and directories currently installed.)
Removing libgettextpo0:i386 ...
Removing libcroco3:i386 ...
Removing libechonest1.2 ...
Removing libprojectm2 ...
Removing libftgl2 ...
Removing libgomp1:i386 ...
Removing libindicate-qt1 ...
Removing libqxt-gui0 ...
Removing libqxt-core0 ...
Removing libunistring0:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: error processing libglib2.0-0:i386 (--configure):
 libglib2.0-0:i386 2.32.3-0ubuntu1 cannot be configured because libglib2.0-0:amd64 is in a different version (2.32.4-0ubuntu1)
dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.32.4-0ubuntu1 cannot be configured because libglib2.0-0:i386 is in a different version (2.32.3-0ubuntu1)
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.32.4-0ubuntu1); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libglib2.0-0 (>= 2.31.8); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on libglib2.0-0; however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
  No apport report written because the error message indicates it's a follow-up error from a previous failure.
    No apport report written because MaxReports has already been reached
                                                                        Errors were encountered while processing:
 libglib2.0-0:i386
 libglib2.0-0
 libglib2.0-bin
 firefox
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)





not sure if relevant i think at some point my root filesystem filled up. have plenty of space now though. have checked it for errors also.

---

### Post by schragge on 2014-12-19
You must break this vicious circle somehow, so let's take it by force:
```

sudo dpkg --force-all --remove libglib2.0-0:i386
sudo apt-get -f install

```

---

### Post by Smiff2 on 2014-12-19
hurray i think we're getting somewhere

>  

 sudo dpkg --force-all --remove libglib2.0-0:i386
[sudo] password for ****: 
dpkg: libglib2.0-0:i386: dependency problems, but removing anyway as you requested:
 wine1.4-i386:i386 depends on libglib2.0-0 (>= 2.16.0).
 libgstreamer0.10-0:i386 depends on libglib2.0-0 (>= 2.31.8).
 libgstreamer-plugins-base0.10-0:i386 depends on libglib2.0-0 (>= 2.31.8).
(Reading database ... 156386 files and directories currently installed.)
Removing libglib2.0-0:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place






> 
sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libgstreamer-plugins-base0.10-0:i386 : Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not going to be installed
 libgstreamer0.10-0:i386 : Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not going to be installed
 wine1.4-i386:i386 : Depends: libglib2.0-0:i386 (>= 2.16.0) but it is not going to be installed
                     Recommends: gettext:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
****@****-GA-MA69VM-S2 ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0:i386
The following NEW packages will be installed
  libglib2.0-0:i386
0 to upgrade, 1 to newly install, 0 to remove and 577 not to upgrade.
4 not fully installed or removed.
Need to get 0 B/1,190 kB of archives.
After this operation, 3,878 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously unselected package libglib2.0-0:i386.
(Reading database ... 156371 files and directories currently installed.)
Unpacking libglib2.0-0:i386 (from .../libglib2.0-0_2.32.4-0ubuntu1_i386.deb) ...
Setting up libglib2.0-0 (2.32.4-0ubuntu1) ...
Setting up libglib2.0-0:i386 (2.32.4-0ubuntu1) ...
Setting up libglib2.0-bin (2.32.4-0ubuntu1) ...
Setting up firefox (32.0.3+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up flashplugin-installer (11.2.202.418ubuntu0.12.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place






> 
sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  flashplugin-installer
1 to upgrade, 0 to newly install, 0 to remove and 576 not to upgrade.
Need to get 7,018 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer amd64 11.2.202.425ubuntu0.12.04.1 [7,018 B]
Fetched 7,018 B in 0s (9,047 B/s)          
Preconfiguring packages ...
(Reading database ... 156387 files and directories currently installed.)
Preparing to replace flashplugin-installer 11.2.202.418ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.425ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.425.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.425.orig.tar.gz)
Installing from local file /tmp/tmpiK8tQO.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.425ubuntu0.12.04.1) ...


thank you!
i tried to report your post for being awesome but there was no option sorry :/

---

