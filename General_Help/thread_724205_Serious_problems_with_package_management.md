---
title: "Serious problems with package management"
date: 2008-03-14
forum: General Help
---

### Post by jis on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/202170](https://bugs.launchpad.net/ubuntu/+bug/202170) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can not install some packages. I am running 32bit version of (X)ubuntu 7.10.
 
I can not install mplayer by " sudo apt-get install mplayer":
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
Depends: libggi2 (>= 1:2.2.1) but it is not installable
Depends: liblame0 (>= 3.97) but it is not installable
Depends: libx264-54 but it is not installable
Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
Depends: mplayer-skins but it is not installable
E: Broken packages

---

### Post by oldos2er on 2008-03-14
Are your software sources enabled? Check System, Administration, Software Sources.

 To fix broken packages, run "sudo aptitude install -f" in a terminal.

---

### Post by jis on 2008-03-14
I have many software sources enabled, including "web" repositories, even if I can not see it in the GUI; it is visible in my sources.list file attached to the launchpad.net page.

I tried "sudo aptitude install -f" in a terminal and it suggest massive installation of NEW packages:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  claws-mail-tnef-parser vmware-server-kernel-source 
The following packages have been automatically kept back:
  libavcodec1d 
The following NEW packages will be installed:
  cdrdao claws-mail-spam-report db2exc debhelper enscript fftw3 gettext gnupg-agent googleearth 
  googleearth-data gpgsm hot-babe html2text intltool-debian k3b kaddressbook kdepim-kio-plugins 
  kdepim-kresources kdeprint kghostview kmail kooka korganizer libaio1 libao2 libcompress-raw-zlib-perl 
  libcompress-zlib-perl libdvdcss2 libgpgme11 libio-compress-base-perl libio-compress-zlib-perl libk3b2 
  libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libmimelib1c2a 
  libmusicbrainz4c2a libpth20 parallels parallels-modules parallels-modules-2.6.22-14-generic 
  parallels-modules-2.6.22-14-server pinentry-qt po-debconf poster postfix procmail psutils vmware-server 
  vmware-server-kernel-modules vmware-server-kernel-modules-2.6.22-14 xinetd 
0 packages upgraded, 58 newly installed, 0 to remove and 1 not upgraded.
Need to get 344MB/367MB of archives. After unpacking 822MB will be used.
The following packages have unmet dependencies:
  claws-mail-tnef-parser: Depends: libytnef0 which is a virtual package.
  vmware-server-kernel-source: Depends: module-assistant which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
claws-mail-tnef-parser [Not Installed]
debhelper [Not Installed]
k3b [Not Installed]
kmail [Not Installed]
kooka [Not Installed]
po-debconf [Not Installed]
vmware-server-kernel-source [Not Installed]

Score is 533

Accept this solution? [Y/n/q/?] 


I don't understand why I should install e.g. googleearth.

---

### Post by oldos2er on 2008-03-14
> **jis said:**
> 
I don't understand why I should install e.g. googleearth.

 I don't either; sorry.

---

### Post by plucky on 2008-03-14
jis,

Is that your **sources.list** posted in the launchpad bug report?

If so you need to edit it and remove the word **web** for each line that looks like > deb [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/) gutsy-backports main restricted universe multiverse **web**

There are 5 lines with the word web in,that needs to be edited to remove web.

then ```
sudo apt-get update
sudo apt-get upgrade
```

Good luck

---

### Post by dsmithnc on 2008-03-14
Not having the exact same problem, but get this when running sudo apt-get upgrade:

Reading state information... Done
The following packages have been kept back:
  kaffeine libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome
  libxine1-misc-plugins libxine1-plugins libxine1-x
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


Can't figure it out.  Hasn't happened before in updating 7.10

Dick

---

### Post by plucky on 2008-03-15
dsmithnc


I don't see any errors,do you have any problem installing software or updates?

Did you do a ```
sudo apt-get update
``` first?

This is the information about **man apt-get upgrade** 
>  upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

Good luck

---

### Post by jis on 2008-03-15
> **plucky said:**
> jis,
Is that your **sources.list** posted in the launchpad bug report?


Yes, it was my source.list; now I removed the "web"s and at least I don't see failures anymore. Thanks.

---

