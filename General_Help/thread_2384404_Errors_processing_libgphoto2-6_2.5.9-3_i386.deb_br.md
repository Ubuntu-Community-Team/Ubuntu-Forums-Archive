---
title: "Errors processing libgphoto2-6_2.5.9-3_i386.deb breaking package system"
date: 2018-02-06
forum: General Help
---

### Post by catsslashgnats on 2018-02-06
Hi,

Whenever try to use Software Updater it tells me the package system is broken. Going through the terminal outputs this:
```
Errors were encountered while processing:
 /var/cache/apt/archives/libgphoto2-6_2.5.9-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Unchecking the Gphoto2 update doesn't help, and I can't install Synaptic because the Software Center stops after a second whenever I try to install it, and I can't compile it myself because it depends on GTK+ which depends on GLib which depends on libmount which I compiled and installed but it says it cannot find. What's the best way to get my updates working again?

---

### Post by cruzer001 on 2018-02-06
The updater says the package system is broken, you say a package is broken.

You also say the terminal says, but is that a update command or a package command you used?

The rant was certainly useful.

Since you didn't tell us, I'm going to guess your running 16.04.  So not really knowing anything my far reaching guess is:

```
sudo apt clean
sudo apt update
sudo apt install libgphoto2-6
```

[http://www.catb.org/esr/faqs/smart-questions.html#beprecise](http://www.catb.org/esr/faqs/smart-questions.html#beprecise)

And welcome to the forums :)

---

### Post by vasa1 on 2018-02-06
Post the entire output of```
sudo apt-get update
```and the entire output of```
sudo apt-get upgrade
```and the output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```and the output of```
uname -a
```and the output of```
lsb_release -a
```

---

### Post by catsslashgnats on 2018-02-07
Yes, I'm on 16.04. I got that output with an update command. Sorry for being unclear. Running those commands gets me this:
```
libgphoto2-6 is already the newest version (2.5.9-3).
libgphoto2-6 set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsane:i386 : Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not going to be installed
 libwine:i386 : Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
And running apt-get -f install gets the error message in the OP.

---

### Post by catsslashgnats on 2018-02-07
sudo apt-get update:
```
Hit:1 http://mirror.lstn.net/ubuntu xenial InReleaseIgn:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://mirror.lstn.net/ubuntu xenial-updates InRelease                   
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://mirror.lstn.net/ubuntu xenial-backports InRelease                 
Hit:6 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:7 http://ppa.launchpad.net/mumble/release/ubuntu xenial InRelease          
Ign:8 https://dl.bintray.com/itchio/deb xenial InRelease                      
Get:10 https://dl.bintray.com/itchio/deb xenial Release [1,840 B]             
Hit:10 https://dl.bintray.com/itchio/deb xenial Release                       
Hit:11 http://ppa.launchpad.net/bartbes/love-stable/ubuntu xenial InRelease   
Hit:12 http://ppa.launchpad.net/jonathonf/wine/ubuntu xenial InRelease       
Hit:14 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease  
Hit:15 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu xenial InRelease     
Reading package lists... Done                      

```

sudo apt-get upgrade:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsane:i386 : Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not installed
 libwine:i386 : Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not installed
E: Unmet dependencies. Try using -f.

```

grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list:
```
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://mirror.lstn.net/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ xenial-security main universe restricted multiverse
/etc/apt/sources.list:deb http://ppa.launchpad.net/mumble/release/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list:deb https://dl.bintray.com/itchio/deb xenial main
/etc/apt/sources.list.d/bartbes-ubuntu-love-stable-xenial.list:deb http://ppa.launchpad.net/bartbes/love-stable/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/jonathonf-ubuntu-wine-xenial.list:deb http://ppa.launchpad.net/jonathonf/wine/ubuntu xenial main
/etc/apt/sources.list.d/obsproject-obs-studio-trusty.list:deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/transmissionbt-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu xenial main

```

uname -a:
```
Linux cody-gaming 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

lsb_release -a:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by cruzer001 on 2018-02-07
I would like to see your sources in a different format, please post the output of:

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

Have you recently added "bintray.com/itchio" or any of your PPAs?

---

### Post by catsslashgnats on 2018-02-07
```
# deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.lstn.net/ubuntu/ xenial main restricted
deb-src http://mirror.lstn.net/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.lstn.net/ubuntu/ xenial-updates main restricted
deb-src http://mirror.lstn.net/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.lstn.net/ubuntu/ xenial universe
deb-src http://mirror.lstn.net/ubuntu/ xenial universe
deb http://mirror.lstn.net/ubuntu/ xenial-updates universe
deb-src http://mirror.lstn.net/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.lstn.net/ubuntu/ xenial multiverse
deb-src http://mirror.lstn.net/ubuntu/ xenial multiverse
deb http://mirror.lstn.net/ubuntu/ xenial-updates multiverse
deb-src http://mirror.lstn.net/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.lstn.net/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirror.lstn.net/ubuntu/ xenial-backports main restricted universe multiverse




## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


# deb http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu xenial main # disabled on upgrade to xenial
deb http://security.ubuntu.com/ubuntu/ xenial-security main universe restricted multiverse
deb http://ppa.launchpad.net/mumble/release/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/mumble/release/ubuntu xenial main
deb https://dl.bintray.com/itchio/deb xenial main
# deb-src https://dl.bintray.com/itchio/deb xenial main
/etc/apt/sources.list.d/bartbes-ubuntu-love-stable-xenial.list
/etc/apt/sources.list.d/fossfreedom-rhythmbox-trusty.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/jonathonf-ubuntu-wine-xenial.list
/etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list
/etc/apt/sources.list.d/nathan-renniewaldock-ubuntu-flux-xenial.list
/etc/apt/sources.list.d/obsproject-obs-studio-trusty.list
/etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-xenial.list
/etc/apt/sources.list.d/openshot_developers-ppa-trusty.list
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list
/etc/apt/sources.list.d/plexmediaserver.list
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list
/etc/apt/sources.list.d/slack.list
/etc/apt/sources.list.d/steam.list
/etc/apt/sources.list.d/transmissionbt-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list
/etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list

```
I've had the itchio PPA for a long time; I don't think any of these are very recent. Thanks for taking a look at this for me.

---

### Post by cruzer001 on 2018-02-07
Ok, time to start with ruling out possible problems.  We will start by temporarily disabling your PPAs.  I do not know if you have access to your sources GUI so here is how to do it in terminal.

Before we start lets make a copy incase Murphy's Law kicks in.  You can remove this after we are finish if you wish or just leave it.  It makes no difference.

```
sudo cp /etc/apt/sources.list.d /etc/apt/sources.list.d.copy
```

Now to disable all PPAs.

```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.bak
```

And try a update/upgrade.  It shouldn't, but if apt complains about this folder missing the just create a new one.

```
sudo mkdir /etc/apt/sources.list.d
```

If this allows you to update/upgrade, please post back.  If this does not then return your PPAs to their normal state.

```
sudo mv /etc/apt/sources.list.d.bak /etc/apt/sources.list.d
```

###########################################################

Next (if the above did nothing).

We do the same thing with your standard sources list.  And again in terminal since I do not know if your GUI will work.

Backup

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.copy
```

I have modified this list for you.  Create a file in your home directory named "sources.list" and copy/paste the below to this new file.


```
# deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.lstn.net/ubuntu/ xenial main restricted
##deb-src http://mirror.lstn.net/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.lstn.net/ubuntu/ xenial-updates main restricted
##deb-src http://mirror.lstn.net/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.lstn.net/ubuntu/ xenial universe
##deb-src http://mirror.lstn.net/ubuntu/ xenial universe
deb http://mirror.lstn.net/ubuntu/ xenial-updates universe
##deb-src http://mirror.lstn.net/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.lstn.net/ubuntu/ xenial multiverse
##deb-src http://mirror.lstn.net/ubuntu/ xenial multiverse
deb http://mirror.lstn.net/ubuntu/ xenial-updates multiverse
##deb-src http://mirror.lstn.net/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.lstn.net/ubuntu/ xenial-backports main restricted universe multiverse
##deb-src http://mirror.lstn.net/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


# deb http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu xenial main # disabled on upgrade to xenial
deb http://security.ubuntu.com/ubuntu/ xenial-security main universe restricted multiverse
##deb http://ppa.launchpad.net/mumble/release/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/mumble/release/ubuntu xenial main
##deb https://dl.bintray.com/itchio/deb xenial main
# deb-src https://dl.bintray.com/itchio/deb xenial main
```

Now move it 

```
sudo mv ~/sources.list /etc/apt/sources.list
```

and update/upgrade

Again if this does nothing for the problem, return to the orginial state.

```
sudo mv /etc/apt/sources.list.copy /etc/apt/sources.list
```

Please be careful, a mistake could add some real confusion.

---

### Post by catsslashgnats on 2018-02-07
Thank you for assisting me with this. Unfortunately neither of these changes affected the outcome.

---

### Post by cruzer001 on 2018-02-07
please post:

```
uname -m
```

```
apt policy multiarch-support
```

Edit

also
```
apt policy libgphoto2-6
```

---

### Post by catsslashgnats on 2018-02-07
uname -m:
```
x86_64

```

apt policy multiarch-support:
```
multiarch-support:  Installed: 2.23-0ubuntu10
  Candidate: 2.23-0ubuntu10
  Version table:
 *** 2.23-0ubuntu10 500
        500 http://mirror.lstn.net/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.23-0ubuntu3 500
        500 http://mirror.lstn.net/ubuntu xenial/main amd64 Packages

```

apt policy libgphoto2-6:
```
libgphoto2-6:  Installed: 2.5.9-3
  Candidate: 2.5.9-3
  Version table:
 *** 2.5.9-3 500
        500 http://mirror.lstn.net/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by cruzer001 on 2018-02-07
Ok, and this:

```
sudo apt-get install libgphoto2-6:i386
```

---

### Post by catsslashgnats on 2018-02-07
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcuda1-375 libllvm4.0 libllvm4.0:i386 linux-headers-4.4.0-101
  linux-headers-4.4.0-101-generic linux-headers-4.4.0-103
  linux-headers-4.4.0-103-generic linux-headers-4.4.0-104
  linux-headers-4.4.0-104-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-91
  linux-headers-4.4.0-91-generic linux-headers-4.4.0-92
  linux-headers-4.4.0-92-generic linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-headers-4.4.0-97
  linux-headers-4.4.0-97-generic linux-headers-4.4.0-98
  linux-headers-4.4.0-98-generic linux-image-4.4.0-101-generic
  linux-image-4.4.0-103-generic linux-image-4.4.0-104-generic
  linux-image-4.4.0-83-generic linux-image-4.4.0-87-generic
  linux-image-4.4.0-89-generic linux-image-4.4.0-91-generic
  linux-image-4.4.0-92-generic linux-image-4.4.0-93-generic
  linux-image-4.4.0-96-generic linux-image-4.4.0-97-generic
  linux-image-4.4.0-98-generic linux-image-extra-4.4.0-101-generic
  linux-image-extra-4.4.0-103-generic linux-image-extra-4.4.0-104-generic
  linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-87-generic
  linux-image-extra-4.4.0-89-generic linux-image-extra-4.4.0-91-generic
  linux-image-extra-4.4.0-92-generic linux-image-extra-4.4.0-93-generic
  linux-image-extra-4.4.0-96-generic linux-image-extra-4.4.0-97-generic
  linux-image-extra-4.4.0-98-generic linux-signed-image-4.4.0-101-generic
  linux-signed-image-4.4.0-103-generic linux-signed-image-4.4.0-104-generic
  linux-signed-image-4.4.0-83-generic linux-signed-image-4.4.0-87-generic
  linux-signed-image-4.4.0-89-generic linux-signed-image-4.4.0-91-generic
  linux-signed-image-4.4.0-92-generic linux-signed-image-4.4.0-93-generic
  linux-signed-image-4.4.0-96-generic linux-signed-image-4.4.0-97-generic
  linux-signed-image-4.4.0-98-generic nvidia-opencl-icd-375
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  gphoto2:i386
The following NEW packages will be installed:
  libgphoto2-6:i386
0 upgraded, 1 newly installed, 0 to remove and 62 not upgraded.
6 not fully installed or removed.
Need to get 0 B/823 kB of archives.
After this operation, 3,647 kB of additional disk space will be used.
(Reading database ... 698599 files and directories currently installed.)
Preparing to unpack .../libgphoto2-6_2.5.9-3_i386.deb ...
Unpacking libgphoto2-6:i386 (2.5.9-3) ...
dpkg: error processing archive /var/cache/apt/archives/libgphoto2-6_2.5.9-3_i386.deb (--unpack):
 trying to overwrite shared '/lib/udev/hwdb.d/20-libgphoto2-6.hwdb', which is different from other instances of package libgphoto2-6:i386
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for udev (229-4ubuntu21) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgphoto2-6_2.5.9-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cruzer001 on 2018-02-07
```
sudo apt autoremove

sudo mv /lib/udev/hwdb.d/20-libgphoto2-6.hwdb /lib/udev/hwdb.d/20-libgphoto2-6.hwdb.old

sudo apt install libgphoto2-6:i386
```

---

### Post by catsslashgnats on 2018-02-08
Brilliant. Everything is working now, thank you so much!

---

### Post by cruzer001 on 2018-02-08
Update and upgrade

Excellent :)

):P

---

