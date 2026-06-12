---
title: "dpkg --unpack error"
date: 2008-02-04
forum: General Help
---

### Post by diegot21 on 2008-02-04
Hi Everyone, I'm having a bit strange error with dpkg.
When I try to install any package using either apt-get install or dpkg -i "package name" I got the following error:

```

dtabar@sarasa:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xine-ui
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1551kB of archives.
After unpacking 3715kB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/xine-ui_0.99.5-2build1_i386.deb (--unpack):
 files list file for package `mktemp' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/xine-ui_0.99.5-2build1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The same thing happens if I try dpkg -i xine-ui_0.9

```

dtabar@sarasa:~$ sudo dpkg -i /var/cache/apt/archives/xine-ui_0.9
dpkg: error processing /var/cache/apt/archives/xine-ui_0.9 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/xine-ui_0.9

```

I think that there is something wrong when dpkg tryies --unpack option, using the mktemp coomand.

The same error occurs with any package I want to install.

I'm running ubuntu 7.10, 2.6.22-14-generic. Any ideas?

---

### Post by taurus on 2008-02-04
What happens if you run the update option first?

```
sudo apt-get update
sudo apt-get install *package_name*
```

Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by diegot21 on 2008-02-04
Hi Taurus, Thanks for replying so quickly!

I tryed to do apt-get update, apt-get install xine-ui with the same results.

this is my sources.list file
```

dtabar@sarasa:/tmp$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
##GNOME-DO REPOS
deb http://ppa.launchpad.net/rharding/ubuntu gutsy main
deb-src http://ppa.launchpad.net/rharding/ubuntu gutsy main
##SKYPE REPOS
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

I have just also tryed to remove a package and get a similar error.
```

dtabar@sarasa:/tmp$ sudo apt-get remove gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-do
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
Need to get 0B of archives.
After unpacking 242kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing gnome-do (--remove):
 files list file for package `mktemp' contains empty filename
Errors were encountered while processing:
 gnome-do
Processing was halted because there were too many errors.

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks For HELPING! :D

---

### Post by diegot21 on 2008-02-08
Well I finally managed to solve this issue, what I did is renaming the directory /var/lib/dpkg/info to /var/lib/dpkg/info_moved, then I recreated the original /var/lib/dpkg/info.

I'm still having some error msgs but I can finally install / uninstall apps.

---

