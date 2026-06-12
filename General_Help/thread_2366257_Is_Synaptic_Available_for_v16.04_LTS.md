---
title: "Is Synaptic Available for v16.04 LTS?"
date: 2017-07-15
forum: General Help
---

### Post by Rick St. George on 2017-07-15
I remember a while back after first upgrading to v16.04, we the community had trouble installing Synaptic Package Manager.

Tried again, it installed, here is the terminal output;

```

5723:/$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libept1.5.0
Suggested packages:
  dwww deborphan
The following NEW packages will be installed:
  libept1.5.0 synaptic
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/1,431 kB of archives.
After this operation, 7,376 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libept1.5.0:amd64.
(Reading database ... 344990 files and directories currently installed.)
Preparing to unpack .../libept1.5.0_1.1+nmu3_amd64.deb ...
Unpacking libept1.5.0:amd64 (1.1+nmu3) ...
Selecting previously unselected package synaptic.
Preparing to unpack .../synaptic_0.83_amd64.deb ...
Unpacking synaptic (0.83) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

Processing triggers for man-db (2.7.5-1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libept1.5.0:amd64 (1.1+nmu3) ...
Setting up synaptic (0.83) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

Processing triggers for menu (2.1.47ubuntu1) ...
5723:/$ 


```


but get the following ERROR message when it comes up!

> 
E: The value 'trusty' is invalid for APT:: Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.


Any ideas?  Is it still not available for v16.04 LTS?  It seems some people were successful (see [https://askubuntu.com/q/805430](https://askubuntu.com/q/805430)).

And if not, how can we check that all depedencies are installed for any particular program or to remove any program, etc. 

Thanks!
Rick
:popcorn:

---

### Post by vasa1 on 2017-07-15
It's available!

```
$ apt policy synaptic
synaptic:
  Installed: 0.83
  Candidate: 0.83
  Version table:
 *** 0.83 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
$  
```

I've never had issues installing Synaptic Package Manager.

Your askubuntu links points to enabling Universe. Simple as that.

---

### Post by Rick St. George on 2017-07-15
Universe is enabled. Not simple as that !?!?!?

---

### Post by vasa1 on 2017-07-15
> **Rick St. George said:**
> Universe is enabled. Not simple as that !?!?!?In your case apparently.```
0 upgraded, 2 newly installed, 0 to remove and **_3_** not upgraded.
```
Let's see the output from ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```and```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by deadflowr on 2017-07-15
Your problem is this problem:
[https://answers.launchpad.net/ubuntu/+question/255926]("https://answers.launchpad.net/ubuntu/+question/255926")
just change out the references of saucy and trusty to trusty and xenial.

---

### Post by monkeybrain20122 on 2017-07-15
Did you upgrade from 14.04?
> [COLOR=#000000]*E: The value 'trusty' is invalid for APT:: Default-Release as such a release is not available in the sources*[/COLOR]

Seems that your sources has been messed up somehow.
```

gksudo gedit /etc/apt/sources.list
```

Change all occurrences of trusty to xenial

Then

```
sudo apt update

sudo apt install synaptic
```

---

### Post by vasa1 on 2017-07-15
> **deadflowr said:**
> Your problem is this problem:
[https://answers.launchpad.net/ubuntu/+question/255926]("https://answers.launchpad.net/ubuntu/+question/255926")
just change out the references of saucy and trusty to trusty and xenial.
Interesting! So this problem carried over to the trusty / xenial as well!

Should OP also run ```
sudo rm /etc/apt/apt.conf
``` as stated in comment #8?

---

### Post by deadflowr on 2017-07-15
> **vasa1 said:**
> Interesting! So this problem carried over to the trusty / xenial as well!

Should OP also run ```
sudo rm /etc/apt/apt.conf
``` as stated in comment #8?

I would think that would be a first step.
If nothing comes of it, then we'll look at other things...

---

### Post by jeremy31 on 2017-07-15
What is the result for ```
ls /usr/lib/nvidia-375
```

---

### Post by Rick St. George on 2017-07-15
output of sources.list

```


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
# deb http://download.bitdefender.com/repos/deb/ bitdefender non-free

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
# deb-src http://deb.opera.com/opera-stable/ stable non-free

```

---

### Post by Rick St. George on 2017-07-15
> **deadflowr said:**
> I would think that would be a first step.
If nothing comes of it, then we'll look at other things...


Output from terminal;

```

5723:~$ sudo rm /etc/apt/apt.conf
[sudo] password for 5723: 
rm: cannot remove '/etc/apt/apt.conf': No such file or directory
5723:~$ 

```


Also Jeremy in answer to your question; output is ...

```

5723:~$ ls /usr/lib/nvidia-375
alt_ld.so.conf                 libnvidia-cfg.so.375.66
bin                            libnvidia-compiler.so
ld.so.conf                     libnvidia-compiler.so.1
libEGL_nvidia.so.0             libnvidia-compiler.so.375.66
libEGL_nvidia.so.375.66        libnvidia-eglcore.so.375.66
libEGL.so                      libnvidia-egl-wayland.so.375.66
libEGL.so.1                    libnvidia-encode.so
libEGL.so.375.66               libnvidia-encode.so.1
libGLdispatch.so.0             libnvidia-encode.so.375.66
libGLESv1_CM_nvidia.so.1       libnvidia-fatbinaryloader.so.375.66
libGLESv1_CM_nvidia.so.375.66  libnvidia-fbc.so
libGLESv1_CM.so                libnvidia-fbc.so.1
libGLESv1_CM.so.1              libnvidia-fbc.so.375.66
libGLESv2_nvidia.so.2          libnvidia-glcore.so.375.66
libGLESv2_nvidia.so.375.66     libnvidia-glsi.so.375.66
libGLESv2.so                   libnvidia-ifr.so
libGLESv2.so.2                 libnvidia-ifr.so.1
libGL.so                       libnvidia-ifr.so.375.66
libGL.so.1                     libnvidia-ml.so
libGL.so.1.0.0                 libnvidia-ml.so.1
libGLX_indirect.so.0           libnvidia-ml.so.375.66
libGLX_nvidia.so.0             libnvidia-ptxjitcompiler.so.375.66
libGLX_nvidia.so.375.66        libnvidia-tls.so.375.66
libGLX.so                      libnvidia-wfb.so.1
libGLX.so.0                    libnvidia-wfb.so.375.66
libnvcuvid.so                  libOpenGL.so
libnvcuvid.so.1                libOpenGL.so.0
libnvcuvid.so.375.66           tls
libnvidia-cfg.so               vdpau
libnvidia-cfg.so.1             xorg

```


Does all this look OK?  See output bottom of page 1 for "sources.list'.

---

### Post by deadflowr on 2017-07-15
Other things to check would be the synaptic.conf file
Unfortunately it's a root file,
(Being the rare root-actual file inside root's home folder at /root/.synaptic/synaptic.conf.
The unfortunate part being to see and read the file you need to sudo)

Look at what 
```
sudo cat /root/.synaptic/synaptic.conf
```
shows.

Yet another reference to the issue:
[http://forums.debian.net/viewtopic.php?f=5&t=126806#p605825]("http://forums.debian.net/viewtopic.php?f=5&t=126806#p605825")

If that's not it, then we'll look again at something else.

---

### Post by vasa1 on 2017-07-16
Let's check```
lsb_release -a
``````
cat /etc/*-release
``````
cat /var/log/installer/media-info
```and```
cat /etc/debian_version
```as well.

---

### Post by jeremy31 on 2017-07-16
Try ```
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.66 /usr/lib/nvidia-375/libEGL.so.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.66 /usr/lib32/nvidia-375/libEGL.so.1
```

Then see if you can install synaptic.  Similar issues have been reported as bugs [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860)

---

### Post by Rick St. George on 2017-07-16
> **jeremy31 said:**
> Try ```
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.66 /usr/lib/nvidia-375/libEGL.so.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.66 /usr/lib32/nvidia-375/libEGL.so.1
```

Then see if you can install synaptic.  Similar issues have been reported as bugs [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860)

Jeremy ... Thanks, but I hesitate doing that because of Post #23 at your Link.[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860/comments/23](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860/comments/23) Mainly;
> The proper solution would be to not install libEGL.so.375.39, as it  is the deprecated non-GLVND implementation. The workaround is therefore  to delete
 rm /usr/{lib,lib32}/nvidia-375/libEGL.so.375.39




Note: in Software & Updates / Additional Drivers / it shows using Nvidia v 375.66 !!!

---

### Post by Rick St. George on 2017-07-16
As to DeadFlower's Requested Output;

```

5723:~$ sudo cat /root/.synaptic/synaptic.conf
Synaptic::ViewMode "3";
Synaptic::showWelcomeDialog "0";
Synaptic::closeZvt "true";
Synaptic::vpanedPos "248";
Synaptic::hpanedPos "203";
Synaptic::windowWidth "1179";
Synaptic::windowHeight "726";
Synaptic::windowX "1636";
Synaptic::windowY "200";
Synaptic::ToolbarState "2";
Synaptic::Maximized "0";
Synaptic::Install-Recommends "1";
Synaptic::update "";
Synaptic::update::last "1461692397";
Synaptic::update::type "0";
Synaptic::LastSearchType "1";
Synaptic::ShowAllPkgInfoInMain "false";
Synaptic::AskRelated "true";
Synaptic::OneClickOnStatusActions "false";
Synaptic::delAction "3";
Synaptic::upgradeType "1";
Synaptic::undoStackSize "20";
Synaptic::UseTerminal "false";
Synaptic::AskQuitOnProceed "false";
Synaptic::useUserFont "0";
Synaptic::useUserTerminalFont "0";
Synaptic::statusColumnPos "0";
Synaptic::statusColumnVisible "1";
Synaptic::supportedColumnPos "1";
Synaptic::supportedColumnVisible "1";
Synaptic::nameColumnPos "2";
Synaptic::nameColumnVisible "1";
Synaptic::sectionColumnPos "3";
Synaptic::sectionColumnVisible "0";
Synaptic::componentColumnPos "4";
Synaptic::componentColumnVisible "0";
Synaptic::instVerColumnPos "5";
Synaptic::instVerColumnVisible "1";
Synaptic::availVerColumnPos "6";
Synaptic::availVerColumnVisible "1";
Synaptic::instSizeColumnPos "7";
Synaptic::instSizeColumnVisible "1";
Synaptic::downloadSizeColumnPos "8";
Synaptic::downloadSizeColumnVisible "0";
Synaptic::descrColumnPos "9";
Synaptic::descrColumnVisible "1";
Synaptic::color-install "#8A8AE2E23434";
Synaptic::color-reinstall "#4E4E9A9A0606";
Synaptic::color-upgrade "#FCFCE9E94F4F";
Synaptic::color-downgrade "#ADAD7F7FA8A8";
Synaptic::color-remove "#EFEF29292929";
Synaptic::color-purge "#A4A400000000";
Synaptic::color-available "";
Synaptic::color-available-locked "#A4A400000000";
Synaptic::color-installed-updated "";
Synaptic::color-installed-outdated "";
Synaptic::color-installed-locked "#A4A400000000";
Synaptic::color-broken "";
Synaptic::color-new "";
Synaptic::UseStatusColors "true";
Synaptic::CleanCache "true";
Synaptic::AutoCleanCache "false";
Synaptic::delHistory "-1";
Synaptic::useProxy "0";
Synaptic::httpProxy "";
Synaptic::httpProxyPort "3128";
Synaptic::ftpProxy "";
Synaptic::ftpProxyPort "3128";
Synaptic::noProxy "";
Synaptic::DefaultDistro "trusty";

```


> **vasa1 said:**
> Let's check```
lsb_release -a
```

OUTPUT: 

```
5723:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

```
cat /etc/*-release
```

OUTPUT:
```
-5723:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

```

```
cat /var/log/installer/media-info
```

OUTPUT:
```
5723:~$ cat /var/log/installer/media-info
Ubuntu-Studio 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.1)
```

and```
cat /etc/debian_version
```

OUTPUT:
```
5723:~$ cat /etc/debian_version
stretch/sid

```


Does this help understand the problem ???  I think I see a problem above under "LSB_release" - it reports No LSB modules are available; and under "installer/media-info" reporting v. 14.04 ?!?

Yes? No? Hhmmm?!?! :(

---

### Post by #&amp;thj^% on 2017-07-16
So I'm guessing here you upgraded from 14.04 to 16.04 then?

---

### Post by mc4man on 2017-07-16
Maybe see what's in this file
```
sudo cat /root/.synaptic/synaptic.conf
```
Your issue with synaptic & the ldconfig stuff on nvidia-375 aren't related. At least here the nvidia thing is of no consequence at all..

---

### Post by Rick St. George on 2017-07-16
> **1fallen said:**
> So I'm guessing here you upgraded from 14.04 to 16.04 then?

CORRECT a while back. Not a fresh install. I let Software Updates handle upgrding to next LTS.

---

### Post by Rick St. George on 2017-07-16
> **mc4man said:**
> Maybe see what's in this file
```
sudo cat /root/.synaptic/synaptic.conf
```
Your issue with synaptic & the ldconfig stuff on nvidia-375 aren't related. At least here the nvidia thing is of no consequence at all..

See First Output on Post #16 above, in request from "DeadFlowr".
Thanks!

---

### Post by #&amp;thj^% on 2017-07-16
> **Rick St. George said:**
> CORRECT a while back. Not a fresh install. I let Software Updates handle upgrding to next LTS.

Not sure if this is still a problem or not, but what dose this show from the terminal:
```
apt policy  apt-xapian-index
```

---

### Post by mrgnome on 2017-07-16
Synaptic is definitely avalible. Have you tried GNOME Software?

---

### Post by mc4man on 2017-07-16
> **Rick St. George said:**
> See First Output on Post #16 above, in request from "DeadFlowr".
Thanks!
you could try getting rid of that line " Synaptic::DefaultDistro "trusty";" 
or just remove synaptic package, remove /root/.synaptic/synaptic.conf, re-install synaptic

---

### Post by Rick St. George on 2017-07-16
> **1fallen said:**
> Not sure if this is still a problem or not, but what dose this show from the terminal:
```
apt policy  apt-xapian-index
```

OUTPUT:

```

5723:~$ apt policy apt-xapian-index
apt-xapian-index:
  Installed: 0.47ubuntu8.3
  Candidate: 0.47ubuntu8.3
  Version table:
 *** 0.47ubuntu8.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     0.47ubuntu8 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```

---

### Post by #&amp;thj^% on 2017-07-16
> **Rick St. George said:**
> OUTPUT:

```

5723:~$ apt policy apt-xapian-index
apt-xapian-index:
  Installed: 0.47ubuntu8.3
  Candidate: 0.47ubuntu8.3
  Version table:
 *** 0.47ubuntu8.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     0.47ubuntu8 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```
If this dose not fix things and I'm sure it won't...I strongly advise what mc4man suggests:
> you could try getting rid of that line " Synaptic::DefaultDistro "trusty";"
or just remove synaptic package, remove /root/.synaptic/synaptic.conf, re-install synaptic 
```
sudo update-apt-xapian-index -vf
```
The code above just force's a rebuild of the index.

---

### Post by vasa1 on 2017-07-16
> **Rick St. George said:**
> ...
Does this help understand the problem ???  I think I see a problem above under "LSB_release" - it reports No LSB modules are available; and under "installer/media-info" reporting v. 14.04 ?!?

Yes? No? Hhmmm?!?! :(No, I think both are fine. "No LSB modules are available" is okay for an updated system. And the "installer/media-info" showing 14.04 points to the medium you used to reach 16.04.

So the mystery remains. BTW, do you have issues installing any other software from the software center?

---

### Post by #&amp;thj^% on 2017-07-17
@ Rick St. George if in doubt about changing the Line with **"Synaptic:: DefaultDistro "trusty";"**
I will show the bottom 5 Lines of mine with offending line removed. (You should be ok making yours the same as I show in mine)
```
 httpProxyPort "3128";
  ftpProxy "";
  ftpProxyPort "3128";
  noProxy "";
};

```
You can use nano to make the changes if you choose to with:
```
sudo nano /root/.synaptic/synaptic.conf
```
Should be pretty straight forward, If not post back.

---

### Post by Rick St. George on 2017-07-17
> **1fallen said:**
> ...I strongly advise what mc4man suggests:

```
sudo update-apt-xapian-index -vf
```
The code above just force's a rebuild of the index.

Followed advice of both. Removed and Purged Synaptic. 
Re-installed, same problem as reported in Post #1.

Any suggestions? What are we doing wrong? Does any of the ouputs suggest something not right?

Thanks for any and all help in this matter.

---

### Post by Rick St. George on 2017-07-17
> **vasa1 said:**
> In your case apparently.```
0 upgraded, 2 newly installed, 0 to remove and **_3_** not upgraded.
```
Let's see the output from ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```and```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Don't believe I replied to this ... so sorry! See OUTPUT below;

```

5723:~$ sudo apt-get update

Hit:1 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease             
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease          
Get:4 http://deb.opera.com/opera-stable stable InRelease [2,592 B]             
Hit:5 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease 
Get:6 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:8 http://deb.opera.com/opera-stable stable/non-free amd64 Packages [1,850 B]
Get:9 http://archive.ubuntu.com/ubuntu xenial-security/universe Sources [36.6 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [59.2 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [49.6 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [145 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [129 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en [74.8 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [40.6 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [56.2 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [164 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [304 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [201 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [505 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [488 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [163 kB]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [212 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Fetched 2,842 kB in 4s (662 kB/s)                                        
Reading package lists... Done

5723:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  python-enum
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

5723:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-xenial.list:deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial main
/etc/apt/sources.list.d/kdenlive-ubuntu-kdenlive-stable-xenial.list.save:deb http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/opera.list.save:deb http://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list.save:deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main

```

Does this help???

---

### Post by vasa1 on 2017-07-17
It's interesting that the *3 not upgraded* has been reduced to *1 not upgraded*.

I'm wondering if one of your ppas has somehow messed things up!

Do you have *[ppa-purge]("http://manpages.ubuntu.com/manpages/xenial/man1/ppa-purge.1.html")* installed? You could use that to temporarily cleanse your system of *all* ppas and the files pulled in with them.

*python-enum* is the package that isn't upgraded.

```
$ apt depends python-enum
python-enum
  Depends: python (>= 2.7)
  Depends: python (<< 2.8)
  Conflicts: python-enum34
09:23 PM ~ $ apt rdepends python-enum
python-enum
Reverse Depends:
  Depends: flashbake (>= 0.4.3)
$ 
```
One other route is to try aptitude instead of apt-get. The former may fix things apt-get can't.

---

### Post by Rick St. George on 2017-07-17
> **vasa1 said:**
> It's interesting that the *3 not upgraded* has been reduced to *1 not upgraded*.

I'm wondering if one of your ppas has somehow messed things up!

Do you have *[ppa-purge]("http://manpages.ubuntu.com/manpages/xenial/man1/ppa-purge.1.html")* installed? You could use that to temporarily cleanse your system of *all* ppas and the files pulled in with them.

*python-enum* is the package that isn't upgraded.

```
$ apt depends python-enum
python-enum
  Depends: python (>= 2.7)
  Depends: python (<< 2.8)
  Conflicts: python-enum34
09:23 PM ~ $ apt rdepends python-enum
python-enum
Reverse Depends:
  Depends: flashbake (>= 0.4.3)
$ 
```
One other route is to try aptitude instead of apt-get. The former may fix things apt-get can't.

I followed the thread here -> [https://ubuntuforums.org/archive/index.php/t-2013200.html](https://ubuntuforums.org/archive/index.php/t-2013200.html) (see last post),
and gave the following command;

```

sudo \rm -fr /root/.synaptic

```

Ran Synaptic Pkg. Mgr. and it came up OK!  Then checked for "python-enum" and upgraded it with Synaptic Pkg. Mgr. 

All should be fine now!  I hope. Thanks all ... Hope this helps someone else!

Will mark closed!
Rick
:P
[URL="https://ubuntuforums.org/archive/index.php/t-2013200.html"]
[/URL]

---

### Post by #&amp;thj^% on 2017-07-17
> **Rick St. George said:**
> 
```

sudo \rm -fr /root/.synaptic

```

Ran Synaptic Pkg. Mgr. and it came up OK!  Then checked for "python-enum" and upgraded it with Synaptic Pkg. Mgr. 

All should be fine now!  I hope. Thanks all ... Hope this helps someone else!

Will mark closed!
Rick
:P
[URL="https://ubuntuforums.org/archive/index.php/t-2013200.html"]
[/URL]
Which is exactly what mc4man suggested :D, Nice job Rick St. George.:D
> or just remove **synaptic package**, Then remove** /root/.synaptic/synaptic.conf**, re-install synaptic
Glad it worked out for you.

---

