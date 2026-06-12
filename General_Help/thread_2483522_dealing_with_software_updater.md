---
title: "dealing with software updater"
date: 2023-02-01
forum: General Help
---

### Post by jgw on 2023-02-01
I decided to update.  I went to the software updater and decided to get rid of everything which was not using the right version.  For me that would be everything not for "jammy".  I used to use y-ppa manager but that has gone away.  I figured that using the software updater and the software updater delete would do.  Now I have created a kindofa disaster.  Here are some of the things I have been getting:

```
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

guvcview: Depends: libc6 (>= 2.34) but 2.35-0ubuntu3.1 is installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.72.4-0ubuntu1 is installed
          Depends: libgtk-3-0 (>= 3.21.4) but 3.24.33-1ubuntu2 is installed
          Depends: libguvcview-2.0-0 but it is not installed
          
greg@greg-hp-8200:~$ sudo apt-get install -f
[sudo] password for greg: 
Sorry, try again.
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libguvcview-2.0-2 libllvm15
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libguvcview-2.0-0
The following NEW packages will be installed:
  libguvcview-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 0 B/130 kB of archives.
After this operation, 364 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 283105 files and directories currently installed.)
Preparing to unpack .../libguvcview-2.0-0_2.0.8+ubuntu2~ppa1+1451-0ubuntu1~202204251847~ubuntu22.04.1_amd64.deb ...
Unpacking libguvcview-2.0-0:amd64 (2.0.8+ubuntu2~ppa1+1451-0ubuntu1~202204251847~ubuntu22.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libguvcview-2.0-0_2.0.8+ubuntu2~ppa1+1451-0ubuntu1~202204251847~ubuntu22.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgviewaudio-2.0.so.2.0.0', which is also in package libguvcview-2.0-2:amd64 2.0.7-2-1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libguvcview-2.0-0_2.0.8+ubuntu2~ppa1+1451-0ubuntu1~202204251847~ubuntu22.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
greg@greg-hp-8200:~$ 

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

guvcview: Depends: libc6 (>= 2.34) but 2.35-0ubuntu3.1 is installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.72.4-0ubuntu1 is installed
          Depends: libgtk-3-0 (>= 3.21.4) but 3.24.33-1ubuntu2 is installed
          Depends: libguvcview-2.0-0 but it is not installed
          
```

As you can see I have a genuine mess on my hands.   I would really appreciate it if somebody could aim me at someplace that will tell me how to fix what I have done.

Thank you...................

---

### Post by oldos2er on 2023-02-02
Your signature says 20.04.x (focal), are you sure you're using 22.04 jammy?

Can you post (in a code box please) the output of ```
cat /etc/apt/sources.list
``` and ```
ls /etc/apt/sources.list.d
```?

---

### Post by jgw on 2023-02-03
Thank you for the reply...

Here is my computer:
```
Computer
Processor	Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
Memory	16270MB (4083MB used)
Machine Type	Mini Tower
Operating System	Ubuntu 22.04.1 LTS
User Name	greg (greg)
Date/Time	Fri 03 Feb 2023 01:03:18 PM PST
Display
Resolution	1920x1080 pixels
OpenGL Renderer	Mesa Intel(R) HD Graphics 2000 (SNB GT1)
X11 Vendor	The X.Org Foundation
Audio Devices
Audio Adapter	HDA-Intel - HDA Intel PCH
```

I screwed up with my signature - apologies.  

Here is what you requested:
[HTML]greg@greg-hp-8200:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819)]/ focal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu jammy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
[/HTML]

[HTML]greg@greg-hp-8200:~$ ls /etc/apt/sources.list.d
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
hluk-ubuntu-copyq-focal.list
hluk-ubuntu-copyq-focal.list.distUpgrade
hluk-ubuntu-copyq-focal.list.save
jcfp-ubuntu-nobetas-focal.list
jcfp-ubuntu-nobetas-focal.list.distUpgrade
jcfp-ubuntu-nobetas-focal.list.save
mkusb-ubuntu-unstable-focal.list
mkusb-ubuntu-unstable-focal.list.distUpgrade
mkusb-ubuntu-unstable-focal.list.save
mozillateam-ubuntu-ppa-jammy.list
mozillateam-ubuntu-ppa-jammy.list.save
nodesource.list
nodesource.list.save
pj-assis-ubuntu-ppa-focal.list
pj-assis-ubuntu-ppa-focal.list.distUpgrade
pj-assis-ubuntu-ppa-focal.list.save
remmina-ppa-team-ubuntu-remmina-next-focal.list
remmina-ppa-team-ubuntu-remmina-next-focal.list.distUpgrade
remmina-ppa-team-ubuntu-remmina-next-focal.list.save
solaar-unifying-ubuntu-stable-jammy.list
solaar-unifying-ubuntu-stable-jammy.list.save
thierry-f-ubuntu-fork-michael-gruz-focal.list
thierry-f-ubuntu-fork-michael-gruz-focal.list.distUpgrade
thierry-f-ubuntu-fork-michael-gruz-focal.list.save
ubuntuhandbook1-ubuntu-apps-focal.list
ubuntuhandbook1-ubuntu-apps-focal.list.distUpgrade
ubuntuhandbook1-ubuntu-apps-focal.list.save
webupd8team-ubuntu-y-ppa-manager-jammy.list
webupd8team-ubuntu-y-ppa-manager-jammy.list.save
greg@greg-hp-8200:~$ [/HTML]

---

