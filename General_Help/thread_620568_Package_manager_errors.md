---
title: "Package manager errors"
date: 2007-11-22
forum: General Help
---

### Post by kuantum_fizax on 2007-11-22
I get errors when I try to install and update packages. Its started with a couple of cups packages, but now more and more don't seem to be working. The weird thing is, package manager says at the bottome 0 broken packages. And it lists the ones I've failed to install as installed. As an example, when I told it to reinstall qt-nethack it gives errors:
E: cupsys: subprocess post-installation script returned error exit status 1
E: gdm: subprocess post-installation script returned error exit status 1
E: nethack-common: subprocess post-installation script returned error exit status 1
E: nethack-qt: dependency problems - leaving unconfigured
E: samba-common: subprocess post-installation script returned error exit status 1
E: smbclient: dependency problems - leaving unconfigured
E: cupsys-bsd: subprocess post-installation script returned error exit status 1

Maybe related, the compiz manager package has been listed as something to be upgraded, but it's always greyed out in the upgrade dialog. I think some dependencies aren't available...

Any advice would be helpful.

---

### Post by rsambuca on 2007-11-22
What does it say when you enter

sudo apt-get update && sudo apt-get upgrade

---

### Post by kuantum_fizax on 2007-11-23
For sudo apt-get update:
**********************************************************************
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
****************************************************************************************

for sudo apt-get upgrade
**********************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up cupsys (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gdm (2.20.1-0ubuntu1) ...
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nethack-common (3.4.3-10.1ubuntu3) ...
dpkg: error processing nethack-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nethack-qt:
 nethack-qt depends on nethack-common (= 3.4.3-10.1ubuntu3); however:
  Package nethack-common is not configured yet.
dpkg: error processing nethack-qt (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.26a-1ubuntu2.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.26a-1ubuntu2.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up cupsys-bsd (1.3.2-1ubuntu7.1) ...
dpkg: error processing cupsys-bsd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
 gdm
 nethack-common
 nethack-qt
 samba-common
 smbclient
 cupsys-bsd
E: Sub-process /usr/bin/dpkg returned an error code (1)
***********************************************************************************************

---

### Post by TidusBlade on 2007-11-23
I remember having such a problem, if it helps maybe you should try doing something with the following:
```
Errors were encountered while processing:
cupsys
gdm
nethack-common
nethack-qt
samba-common
smbclient
cupsys-bsd
```
That could be your problem.... reinstalling them or something like that could work...
Hope it works ;)

---

### Post by kuantum_fizax on 2007-11-23
thanks titusblade, but that's actually what I mentioned I was doing in the first post.  I've tried to reinstall cups-sys and the nethack stuff, but I get the same errors.

---

### Post by kuantum_fizax on 2007-11-26
To be clear, I'm still having the problem. Any other help guys? THanks

---

### Post by bpazolli on 2007-12-02
bump I have the same problem

---

### Post by Luke771 on 2007-12-06
Same problem here.
Uninstalling tzdata is a bad idea  because that wouldr remove essential packages, and reinstalling it is blocked as anything related to installing, uninstalling, updating.

The problem appeard for the first time this moring when update-manager flashed a notice about available updates, I ran it, and the upddates got installed, all but one:  libcompress-zlib-perl -then the error message about tzdata popped up. Since then, I can't install, uninstall, reinstall or upgrade anything; same result for apt, synaptic and update-manager;
```

E: tzdata: subprocess post-installation script returned error exit status 1

```

---

### Post by Jumpmasterrt on 2007-12-06
I had the same thing happen to me, only it started with a Perl Update. 

I thought I had fixed the broken packages but it only uninstalled my whole gnome gui. 

Anyway, I reinstalled (since I hadn't started really using it yet cause it's not set up properly) so the only loss was time.

---

### Post by Luke771 on 2007-12-07
I tried to do the obvous and reinstall tzdata as the error that was blocking everything was in there.

But when I tried to do that, the error in tzdata would block the reinstallation of tzdata itself, so after a couple of frustrating trys, I eventually realized what the obvious #2 would be: check the output.

I tried to reinstall tzdata again, using Synaptic, and when I got the message 'Error in the package tzdata' I clicked 'details'.
I couldn't copy - paste from Synaptic's 'details' window (after the error message) and it was too long to copy by hand, but the point was that the error was about tzdata not being able to find a directory and a .dat file, that were supposed to be located in /var/log and /var/cache respectively.

The problem was that when I cleaned all the 'junk' from my Ubuntu, I had unawarely deleted some files and directories that some packages actually need.
At this point my first try was to create those directories and also create an empty file called config.dat and hope that finding the file in place was everything tzdata needed in order to work.
It did.
After having created directories and config.dat, I reinstalled tzdata and it worked, run the update manager and the updates got installed. Here is what to create;

```


sudo mkdir /var/log/apt


 sudo mkdir -p /var/cache/debconf


```

-p means 'progressive' (or something): make all those direcotries one into another.
Also you need to create an empry file into /var/cache/debconf and call it config.dat.
You need to do everything as root because you can't write outside of your home dir as user.

[edit: typo]

---

### Post by kuantum_fizax on 2007-12-09
Thanks luke, hopefully that helps someone else, but that doesn't seem to solve my problem... I have those files and directories already.

Apparently I really screwed up my package manager somehow...

---

### Post by kuantum_fizax on 2007-12-22
Any other ideas? I guess I'll reinstall linux soon, which really stinks because I've invested so much time adjusting it to work like I like.

---

