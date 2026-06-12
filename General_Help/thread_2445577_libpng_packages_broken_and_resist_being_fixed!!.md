---
title: "libpng packages broken and resist being fixed!?!"
date: 2020-06-16
forum: General Help
---

### Post by crazybear on 2020-06-16
There are three broken packages that [I believe] need to be upgraded, but I can't - I get the error message below. I can't do anything with them - have tried everything I know. They are all libpng packages and there are newer versions. [see image of the three of them].
Anyone able to help me out?! It is  causing some problems and making the installation of other updates problematic.
Thanks.

Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1.1_amd64.deb ...
Unpacking libpng12-0:amd64 (1.2.54-1ubuntu1.1) over (1.2.54-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libpng12-0/changelog.Debian.gz', which is different from other instances of package libpng12-0:amd64
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package libpng12-0:amd64 (--configure):
 package libpng12-0:amd64 1.2.54-1ubuntu1 cannot be configured because libpng12-0:i386 is at a different version (1.2.54-1ubuntu1.1)
dpkg: error processing package libpng12-0:i386 (--configure):
 package libpng12-0:i386 1.2.54-1ubuntu1.1 cannot be configured because libpng12-0:amd64 is at a different version (1.2.54-1ubuntu1)
dpkg: dependency problems prevent configuration of sane-utils:
 sane-utils depends on libpng12-0 (>= 1.2.13-4); however:
  Package libpng12-0:amd64 is not configured yet.

dpkg: error processing package sane-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt3-mt:
 libqt3-mt depends on libpng12-0 (>= 1.2.13-4); however:
  Package libpng12-0:amd64 is not configured yet.

dpkg: error processing package libqt3-mt (--configure):
 dependency problems - leaving unconfigured

---

### Post by Impavidus on 2020-06-17
It says that the package cannot be configured because the 32 bit and 64 bit editions are at different version numbers. Which is weird, as both should be at version 1.2.54-1ubuntu1.1. Maybe a race condition during refresh? Never seen this before. Try this:```
sudo apt update
sudo apt upgrade
```Maybe that will bring the 64 bit version to 1.2.54-1ubuntu1.1 too.

I assume this is Ubuntu 16.04?

---

### Post by crazybear on 2020-06-20
Thanks for the help. The system did not send me an email there was an answer....but I just looked and found yours. However, your suggested 'fix' didn't work [although it did allow a lot of blocked packages to be installed]. This is frustrating!...and it was blocking the installation of most other packages. I've tried everything in Synaptic - but nothing works. Other ideas?

sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.54-1ubuntu1) but 1.2.54-1ubuntu1.1 is installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
 libpng12-dev : Depends: libpng12-0 (= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
E: Unmet dependencies. Try using -f
Errors were encountered while processing:
 /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by crazybear on 2020-06-20
Just tried 'Fix Broken Packages' in Synaptic. It did a LOT of stuff, but ended with:
E: /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb: trying to overwrite shared '/usr/share/doc/libpng12-0/changelog.Debian.gz', which is different from other instances of package libpng12-0:amd64

I'm stuck and can't see how to move forward. libpng12-0 will not update!!!

---

### Post by monkeybrain20122 on 2020-06-20
Have you added a ppa and then disabled it? Seems like your sources are out of sync.

---

### Post by Impavidus on 2020-06-20
Let's have a look at those sources:```
apt-cache policy libpng12-0 libpng12-dev
```
Do you actually need the 32 bit version of libpng?

---

### Post by crazybear on 2020-06-21
**$ apt-cache policy libpng12-0 libpng12-dev**
libpng12-0:
  Installed: 1.2.54-1ubuntu1
  Candidate: 1.2.54-1ubuntu1.1
  Version table:
     1.2.54-1ubuntu1.1 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
 *** 1.2.54-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1.2.46-3ubuntu4 500
        500 [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) precise/main amd64 Packages
libpng12-dev:
  Installed: 1.2.54-1ubuntu1.1
  Candidate: 1.2.54-1ubuntu1.1
  Version table:
 *** 1.2.54-1ubuntu1.1 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.2.54-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
     1.2.46-3ubuntu4 500
        500 [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) precise/main amd64 Packages

I don't understand why anything would be from 'precise' - that was 12.04!?!

---

### Post by ajgreeny on 2020-06-21
So let's  see your sources.list content with output of

cat /etc/apt/sources.list

Perhaps you just need to delete those "precise" lines.

---

### Post by crazybear on 2020-06-21
No, That doesn't seem to be the problem....

$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main universe multiverse restricted
deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) xenial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports universe multiverse restricted main
deb [arch=amd64] [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib
deb [https://packagecloud.io/Enrico204/Whatsapp-Desktop/debian/](https://packagecloud.io/Enrico204/Whatsapp-Desktop/debian/) stretch main

---

### Post by ajgreeny on 2020-06-21
Perhaps that source is in a sources.list.d file?

---

### Post by Impavidus on 2020-06-21
Is it not possible to tell apt to upgrade the 64 bit package before attempting anything else?```
sudo apt-get upgrade libpng12-0:amd64
```I don't mix 32 bit and 64 bit.

Otherwise, you might try temporarily removing the 32 bit version, then upgrade the 64 bit version, then reinstall the 32 bit version.

---

### Post by crazybear on 2020-06-21
I don't understand the implication nor what I'd do with your question......

---

### Post by crazybear on 2020-06-21
> **Impavidus said:**
> Is it not possible to tell apt to upgrade the 64 bit package before attempting anything else?```
sudo apt-get upgrade libpng12-0:amd64
```I don't mix 32 bit and 64 bit.

Otherwise, you might try temporarily removing the 32 bit version, then upgrade the 64 bit version, then reinstall the 32 bit version.

No, This suggestion was one of the first I tried long ago. The frightening thing is when I try to mark the 32 bit version for removal, it also marks about 100+ packages for removal...I just fear a lot of damage could be done and not easy to repair.......

Despite my fear, I tried to delete it. System won't allow it to be deleted.... Ideas anyone?! I'm stuck with 3 broken packages.
----------------------------------
$ sudo apt-get upgrade libpng12-0:amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.54-1ubuntu1) but 1.2.54-1ubuntu1.1 is installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
 libpng12-dev : Depends: libpng12-0 (= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

$ sudo apt-get -f install
[sudo] password for peter-and-crazybear: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  liblilv-0-0 libmysqlclient18 libserd-0-0 libsord-0-0 libsratom-0-0
  libsuil-0-0 linux-headers-4.15.0-99 linux-headers-4.15.0-99-generic
  linux-image-4.15.0-99-generic linux-modules-4.15.0-99-generic
  linux-modules-extra-4.15.0-99-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libpng12-0
The following packages will be upgraded:
  libpng12-0
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0 B/116 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 705149 files and directories currently installed.)
Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1.1_amd64.deb ...
Unpacking libpng12-0:amd64 (1.2.54-1ubuntu1.1) over (1.2.54-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libpng12-0/changelog.Debian.gz', which is different from other instances of package libpng12-0:amd64
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by crazybear on 2020-06-22
Please someone, I appreciate the help so far, but so far none of the suggestions have worked and/or I had already tried them. I'm stuck and can not update  any package with these broken packages. Also can't remove the one that is causing the problem - nor update it. HELP! PLEASE! There has to be a way through this mess....but I certainly do NOT know what it is. I've tried all of the suggestions and some of my own MULTIPLE times and everytime get the same error messages and libpng12-0 NOT updating, not able to be removed or reinstalled. STUCK!!!

Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1.1_amd64.deb ... 
Unpacking libpng12-0:amd64 (1.2.54-1ubuntu1.1) over (1.2.54-1ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb (--unpack): 
 trying to overwrite shared '/usr/share/doc/libpng12-0/changelog.Debian.gz', which is different from other instances of package libpng12-0:amd64 
Processing triggers for libc-bin (2.23-0ubuntu11) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb 
dpkg: error processing package libpng12-0:amd64 (--configure): 
 package libpng12-0:amd64 1.2.54-1ubuntu1 cannot be configured because libpng12-0:i386 is at a different version (1.2.54-1ubuntu1.1) 
dpkg: error processing package libpng12-0:i386 (--configure): 
 package libpng12-0:i386 1.2.54-1ubuntu1.1 cannot be configured because libpng12-0:amd64 is at a different version (1.2.54-1ubuntu1) 
dpkg: dependency problems prevent configuration of sane-utils: 
 sane-utils depends on libpng12-0 (>= 1.2.13-4); however: 
  Package libpng12-0:amd64 is not configured yet. 
 
dpkg: error processing package sane-utils (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libqt3-mt: 
 libqt3-mt depends on libpng12-0 (>= 1.2.13-4); however: 
  Package libpng12-0:amd64 is not configured yet. 
 
dpkg: error processing package libqt3-mt (--configure): 
 dependency problems - leaving unconfigured

---

### Post by ActionParsnip on 2020-06-22
Did you edit your sources.list file to upgrade direct from Precise to Xenial, by any chance?

---

### Post by crazybear on 2020-06-22
> **ActionParsnip said:**
> Did you edit your sources.list file to upgrade direct from Precise to Xenial, by any chance?

Hmmm......I searched for 'sources.list' and there are many such files. Most are templates with all entries #'d out.
However, one called sources.list.distUpgrade is all Trusty sources. Should I just delete that entire file or edit 'trusty' to 'xenial'?
Another, sources.list.d has mostly xenial, but some that are trusty and some that don't say....but it is a VERY long list. How would I edit it so that every entry with trusty were eliminated [the entire line] or again would I want to replace trusty with xenial in every case?
I'm assuming that if that source doesn't exist in xenial, it will just be ignored...but I'd like to know before I create problems.
There are some older programs I run that I know existed on trusty and do not exist on xenial - and I like them. I didn't think it was a problem for them to still be there. Would anyone know EXACTLY which source is causing my problem with libpng? I assume a main one. A lot of my sources are for individual programs of an arcane type I like and use.

---

### Post by Impavidus on 2020-06-23
Have you tried removing the 32 bit libpng using dpkg?```
sudo dpkg -r libpng12-0:i386
```dpkg can do such things even when that causes a package conflict, which may be the case. I guess you may have some arcane packages depending on 32 bit libraries. If you manage to remove the 32 bit libpng, it should be possible to upgrade the 64 bit version, then reinstall the 32 bit version.

Keeping software from old releases may cause package conflicts. It looks like your system is quite dirty. Xenial is still supported for 10 months, so we try to help you, but I wouldn't invest too much time in an old system. And don't attempt to upgrade to the next release. When you want to move, make it a fresh install and skip 18.04.

---

### Post by ajgreeny on 2020-06-23
The important sources.list file is /etc/apt/sources.list and you have shown us the content of that.
I do not know if the debian repo you have enabled is causing problems, or maybe even supplying that errant libpng package but it appears from your apt-cacahe policy command above that it came from the [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) precise/main amd64 repository, and even though that is not in your sources.list file, I wonder if it is in a file in the ***/etc/apt/sources.list.d*** folder; you have not shown us any content of that so far.

---

### Post by Impavidus on 2020-06-23
There is a precise repository mentioned by apt-cache for libpng12-0, but the currently installed versions come from xenial (amd64) and xenial-updates (i386).

---

### Post by crazybear on 2020-06-24
As I said above, in the /etc/apt/sources.list.d there are many trusty mentions and lots of xenial too. I do NOT know how to copy and post it here - I've tried and it resists being copied. Should there be no trusty sources listed and if so how to I remove them or change them all to xenial?

---

### Post by crazybear on 2020-06-24
> **Impavidus said:**
> Have you tried removing the 32 bit libpng using dpkg?```
sudo dpkg -r libpng12-0:i386
```dpkg can do such things even when that causes a package conflict, which may be the case. I guess you may have some arcane packages depending on 32 bit libraries. If you manage to remove the 32 bit libpng, it should be possible to upgrade the 64 bit version, then reinstall the 32 bit version.

Keeping software from old releases may cause package conflicts. It looks like your system is quite dirty. Xenial is still supported for 10 months, so we try to help you, but I wouldn't invest too much time in an old system. And don't attempt to upgrade to the next release. When you want to move, make it a fresh install and skip 18.04.

As I mentioned above, this is NOT possible to do. If you know some secret  way to force its removal it let me know.

$ sudo dpkg -r libpng12-0:i386
[sudo] password for peter-and-crazybear: 
dpkg: dependency problems prevent removal of libpng12-0:i386:
 libqtwebkit4:i386 depends on libpng12-0 (>= 1.2.13-4).
 libsdl-image1.2:i386 depends on libpng12-0 (>= 1.2.13-4).
 gstreamer0.10-plugins-good:i386 depends on libpng12-0 (>= 1.2.13-4).
 libcupsfilters1:i386 depends on libpng12-0 (>= 1.2.13-4).
 libfreetype6:i386 depends on libpng12-0 (>= 1.2.13-4).
 libgd3:i386 depends on libpng12-0 (>= 1.2.13-4).
 libgdk-pixbuf2.0-0:i386 depends on libpng12-0 (>= 1.2.13-4).
 libqtgui4:i386 depends on libpng12-0 (>= 1.2.13-4).
 libcairo2:i386 depends on libpng12-0 (>= 1.2.13-4).

dpkg: error processing package libpng12-0:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libpng12-0:i386

---

### Post by westie457 on 2020-06-24
> **crazybear said:**
> As I said above, in the /etc/apt/sources.list.d there are many trusty mentions and lots of xenial too. I do NOT know how to copy and post it here - I've tried and it resists being copied. Should there be no trusty sources listed and if so how to I remove them or change them all to xenial?

```
ls /etc/apt/sources.list.d
```will list those files.
Careful use of 'sudo rm /etc/apt/sources.list.d/"nameoffile"' will remove that file. Not so careful use of 'sudo rm' will do serious harm to your system.
Renaming of files outside of the Home directory I have no idea either.

---

### Post by crazybear on 2020-06-25
> **westie457 said:**
> ```
ls /etc/apt/sources.list.d
```will list those files.
Careful use of 'sudo rm /etc/apt/sources.list.d/"nameoffile"' will remove that file. Not so careful use of 'sudo rm' will do serious harm to your system.
Renaming of files outside of the Home directory I have no idea either.

The list is VERY long and there are MANY trusty on it. Do I want to delete all 'trusty'? Could it cause programs I use stop working? If all should be removed is there a way to do so with ONE command?...doing it individually will take hours....but my first question is the more important. Why does each seem to have two or three versions - one with .save on it? some with .distUpgrade? Some few don't mention trusty nor xenial. 

```

$ ls /etc/apt/sources.list.d
abiword-stable-ubuntu-ppa-xenial.list
abiword-stable-ubuntu-ppa-xenial.list.save
alexlarsson-ubuntu-flatpak-xenial.list
alexlarsson-ubuntu-flatpak-xenial.list.save
alexmurray-indicator-sensors-daily-trusty.list
alexmurray-indicator-sensors-daily-trusty.list.distUpgrade
alexmurray-indicator-sensors-daily-trusty.list.save
alexmurray-indicator-sensors-trusty.list
alexmurray-indicator-sensors-trusty.list.distUpgrade
alexmurray-indicator-sensors-trusty.list.save
alexmurray-ubuntu-indicator-sensors-xenial.list
alexmurray-ubuntu-indicator-sensors-xenial.list.save
AllToMP3_alltomp3.list
AllToMP3_alltomp3.list.save
apandada1-ubuntu-typhoon-xenial.list
apandada1-ubuntu-typhoon-xenial.list.save
atareao-atareao-trusty.list
atareao-atareao-trusty.list.distUpgrade
atareao-atareao-trusty.list.save
atareao-ubuntu-atareao-xenial.list
atareao-ubuntu-atareao-xenial.list.save
audacity-team-ubuntu-daily-xenial.list
audacity-team-ubuntu-daily-xenial.list.save
a-v-shkop-ubuntu-chromium-xenial.list
a-v-shkop-ubuntu-chromium-xenial.list.save
banshee-team-ppa-trusty.list
banshee-team-ppa-trusty.list.distUpgrade
banshee-team-ppa-trusty.list.save
b-eltzner-qpdfview-trusty.list
b-eltzner-qpdfview-trusty.list.distUpgrade
b-eltzner-qpdfview-trusty.list.save
bhdouglass-indicator-remindor-trusty.list
bhdouglass-indicator-remindor-trusty.list.distUpgrade
bhdouglass-indicator-remindor-trusty.list.save
bhdouglass-ubuntu-indicator-remindor-xenial.list
bhdouglass-ubuntu-indicator-remindor-xenial.list.save
brave.list
brave.list.save
caffeine-developers-caffeine-dev-trusty.list
caffeine-developers-caffeine-dev-trusty.list.distUpgrade
caffeine-developers-caffeine-dev-trusty.list.save
caffeine-developers-ppa-trusty.list
caffeine-developers-ppa-trusty.list.distUpgrade
caffeine-developers-ppa-trusty.list.save
cfgnunes-ppa-trusty.list
cfgnunes-ppa-trusty.list.distUpgrade
cfgnunes-ppa-trusty.list.save
cfgnunes-ubuntu-ppa-xenial.list
cfgnunes-ubuntu-ppa-xenial.list.save
danielrichter2007-grub-customizer-trusty.list
danielrichter2007-grub-customizer-trusty.list.distUpgrade
danielrichter2007-grub-customizer-trusty.list.save
deluge-team-ppa-trusty.list
deluge-team-ppa-trusty.list.distUpgrade
deluge-team-ppa-trusty.list.save
deluge-team-ubuntu-ppa-xenial.list
deluge-team-ubuntu-ppa-xenial.list.save
do-core-ubuntu-ppa-xenial.list
do-core-ubuntu-ppa-xenial.list.save
ehoover-compholio-trusty.list
ehoover-compholio-trusty.list.distUpgrade
ehoover-compholio-trusty.list.save
embrosyn-ubuntu-cinnamon-xenial.list
embrosyn-ubuntu-cinnamon-xenial.list.save
extra.list
extra.list.save
fixnix-ubuntu-netspeed-xenial.list
fixnix-ubuntu-netspeed-xenial.list.save
freecad-maintainers-ubuntu-freecad-daily-xenial.list
freecad-maintainers-ubuntu-freecad-daily-xenial.list.save
freecad-maintainers-ubuntu-freecad-stable-xenial.list
freecad-maintainers-ubuntu-freecad-stable-xenial.list.save
freetuxtv-ubuntu-freetuxtv-dev-xenial.list
freetuxtv-ubuntu-freetuxtv-dev-xenial.list.save
george-edison55-ubuntu-nitroshare-xenial.list
george-edison55-ubuntu-nitroshare-xenial.list.save
getdeb.list
getdeb.list.distUpgrade
getdeb.list.save
gezakovacs-ubuntu-ppa-xenial.list
gezakovacs-ubuntu-ppa-xenial.list.save
gnac-team-ubuntu-ppa-xenial.list
gnac-team-ubuntu-ppa-xenial.list.save
gnome3-team-gnome3-trusty.list
gnome3-team-gnome3-trusty.list.distUpgrade
gnome3-team-gnome3-trusty.list.save
gnome3-team-ubuntu-gnome3-xenial.list
gnome3-team-ubuntu-gnome3-xenial.list.save
google-earth.list
google-earth.list.save
google-earth-pro.list
google-earth-pro.list.save
graphics-drivers-ubuntu-ppa-xenial.list
graphics-drivers-ubuntu-ppa-xenial.list.save
heyarje-ubuntu-libav-11-xenial.list
heyarje-ubuntu-libav-11-xenial.list.save
hsoft-ubuntu-ppa-xenial.list
hsoft-ubuntu-ppa-xenial.list.save
inameiname-ubuntu-stable-xenial.list
inameiname-ubuntu-stable-xenial.list.save
indicator-multiload-stable-daily-trusty.list
indicator-multiload-stable-daily-trusty.list.distUpgrade
indicator-multiload-stable-daily-trusty.list.save
jd-team-ubuntu-jdownloader-xenial.list
jd-team-ubuntu-jdownloader-xenial.list.save
jfi-psensor-unstable-trusty.list
jfi-psensor-unstable-trusty.list.distUpgrade
jfi-psensor-unstable-trusty.list.save
jonathonf-ubuntu-vlc-xenial.list
jonathonf-ubuntu-vlc-xenial.list.save
jre-phoenix-ppa-trusty.list
jre-phoenix-ppa-trusty.list.distUpgrade
jre-phoenix-ppa-trusty.list.save
kazam-team-ubuntu-unstable-series-xenial.list
kazam-team-ubuntu-unstable-series-xenial.list.save
kazam-team-unstable-series-trusty.list
kazam-team-unstable-series-trusty.list.distUpgrade
kazam-team-unstable-series-trusty.list.save
kokoto-java-ubuntu-omgubuntu-stuff-xenial.list
kokoto-java-ubuntu-omgubuntu-stuff-xenial.list.save
libdvdcss.list
libdvdcss.list.distUpgrade
libdvdcss.list.save
libratbag-piper-ubuntu-piper-libratbag-git-xenial.list
libratbag-piper-ubuntu-piper-libratbag-git-xenial.list.save
libreoffice-ppa-trusty.list
libreoffice-ppa-trusty.list.distUpgrade
libreoffice-ppa-trusty.list.save
libreoffice-ubuntu-libreoffice-3-5-xenial.list
libreoffice-ubuntu-libreoffice-3-5-xenial.list.save
libreoffice-ubuntu-libreoffice-4-4-xenial.list
libreoffice-ubuntu-libreoffice-4-4-xenial.list.save
linuxuprising-ubuntu-apps-xenial.list
linuxuprising-ubuntu-apps-xenial.list.save
lubuntu-desktop-ubuntu-ppa-xenial.list
lubuntu-desktop-ubuntu-ppa-xenial.list.save
matrix-riot-im.list
matrix-riot-im.list.save
mc3man-mplayer-test-trusty.list
mc3man-mplayer-test-trusty.list.distUpgrade
mc3man-mplayer-test-trusty.list.save
mc3man-trusty-media-trusty.list
mc3man-trusty-media-trusty.list.distUpgrade
mc3man-trusty-media-trusty.list.save
michael-gruz-canon-trunk-trusty.list
michael-gruz-canon-trunk-trusty.list.distUpgrade
michael-gruz-canon-trunk-trusty.list.save
michael-gruz-ubuntu-canon-xenial.list
michael-gruz-ubuntu-canon-xenial.list.save
mixxx-mixxx-trusty.list
mixxx-mixxx-trusty.list.distUpgrade
mixxx-mixxx-trusty.list.save
mixxx-ubuntu-mixxx-xenial.list
mixxx-ubuntu-mixxx-xenial.list.save
mizuno-as-ubuntu-gimp-painter-xenial.list
mizuno-as-ubuntu-gimp-painter-xenial.list.save
muravjov-il-ubuntu-ppa-xenial.list
muravjov-il-ubuntu-ppa-xenial.list.save
nextcloud-devs-ubuntu-client-xenial.list
nextcloud-devs-ubuntu-client-xenial.list.save
nilarimogard-ubuntu-webupd8-xenial.list
nilarimogard-ubuntu-webupd8-xenial.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.distUpgrade
nilarimogard-webupd8-trusty.list.save
n-muench-programs-ppa-trusty.list
n-muench-programs-ppa-trusty.list.distUpgrade
n-muench-programs-ppa-trusty.list.save
n-muench-ubuntu-calibre2-xenial.list
n-muench-ubuntu-calibre2-xenial.list.save
n-muench-ubuntu-programs-ppa-xenial.list
n-muench-ubuntu-programs-ppa-xenial.list.save
noobslab-indicators-trusty.list
noobslab-indicators-trusty.list.distUpgrade
noobslab-indicators-trusty.list.save
openshot_developers-ubuntu-ppa-xenial.list
openshot_developers-ubuntu-ppa-xenial.list.save
opera-developer.list
opera-developer.list.distUpgrade
opera-developer.list.save
osmoma-audio-recorder-trusty.list
osmoma-audio-recorder-trusty.list.distUpgrade
osmoma-audio-recorder-trusty.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.distUpgrade
otto-kesselgulasch-gimp-trusty.list.save
pascal-bach-ubuntu-unison-xenial.list
pascal-bach-ubuntu-unison-xenial.list.save
paulo-miguel-dias-ubuntu-pkppa-xenial.list
paulo-miguel-dias-ubuntu-pkppa-xenial.list.save
pidgin-developers-ppa-trusty.list
pidgin-developers-ppa-trusty.list.save
pidgin-ppa.list
pidgin-ppa.list.distUpgrade
pidgin-ppa.list.save
playdeb.list
playdeb.list.distUpgrade
playdeb.list.save
plushuang-tw-ubuntu-uget-stable-xenial.list
plushuang-tw-ubuntu-uget-stable-xenial.list.save
plushuang-tw-uget-stable-trusty.list
plushuang-tw-uget-stable-trusty.list.distUpgrade
plushuang-tw-uget-stable-trusty.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_allvideodownloader_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_outreel_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_outreel_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_outreel_ubuntu.list.save
ring-nightly-man.list
ring-nightly-man.list.save
rolfbensch-ubuntu-sane-git-xenial.list
rolfbensch-ubuntu-sane-git-xenial.list.save
samoilov-lex-ubuntu-aftl-stable-xenial.list
samoilov-lex-ubuntu-aftl-stable-xenial.list.save
screenlets-ppa-trusty.list
screenlets-ppa-trusty.list.distUpgrade
screenlets-ppa-trusty.list.save
serge-rider-ubuntu-dbeaver-ce-xenial.list
serge-rider-ubuntu-dbeaver-ce-xenial.list.save
shnatsel-ubuntu-gimp-paint-studio-xenial.list
shnatsel-ubuntu-gimp-paint-studio-xenial.list.save
shutter-ppa-trusty.list
shutter-ppa-trusty.list.distUpgrade
shutter-ppa-trusty.list.save
skunk-ubuntu-pepper-flash-xenial.list
skunk-ubuntu-pepper-flash-xenial.list.save
skype-stable.list
skype-stable.list.save
skype-wrapper-ppa-trusty.list
skype-wrapper-ppa-trusty.list.distUpgrade
skype-wrapper-ppa-trusty.list.save
sneetsher-ubuntu-copies-xenial.list
sneetsher-ubuntu-copies-xenial.list.save
stebbins-handbrake-snapshots-trusty.list
stebbins-handbrake-snapshots-trusty.list.distUpgrade
stebbins-handbrake-snapshots-trusty.list.save
team-xbmc-ppa-trusty.list
team-xbmc-ppa-trusty.list.distUpgrade
team-xbmc-ppa-trusty.list.save
team-xbmc-ubuntu-ppa-xenial.list
team-xbmc-ubuntu-ppa-xenial.list.save
teejee2008-ppa-trusty.list
teejee2008-ppa-trusty.list.distUpgrade
teejee2008-ppa-trusty.list.save
teejee2008-ubuntu-ppa-xenial.list
teejee2008-ubuntu-ppa-xenial.list.save
telepathy-ubuntu-ppa-xenial.list
telepathy-ubuntu-ppa-xenial.list.save
thebernmeister-ppa-trusty.list
thebernmeister-ppa-trusty.list.distUpgrade
thebernmeister-ppa-trusty.list.save
thebernmeister-ubuntu-ppa-xenial.list
thebernmeister-ubuntu-ppa-xenial.list.save
thierry-f-ubuntu-fork-michael-gruz-xenial.list
thierry-f-ubuntu-fork-michael-gruz-xenial.list.save
thomas_tsai-ubuntu-ubuntu-tuxboot-xenial.list
thomas_tsai-ubuntu-ubuntu-tuxboot-xenial.list.save
tiheum-equinox-trusty.list
tiheum-equinox-trusty.list.distUpgrade
tiheum-equinox-trusty.list.save
transmissionbt-ppa-trusty.list
transmissionbt-ppa-trusty.list.distUpgrade
transmissionbt-ppa-trusty.list.save
transmissionbt-ubuntu-ppa-xenial.list
transmissionbt-ubuntu-ppa-xenial.list.save
tualatrix-ppa-trusty.list
tualatrix-ppa-trusty.list.distUpgrade
tualatrix-ppa-trusty.list.save
tualatrix-ubuntu-ppa-xenial.list
tualatrix-ubuntu-ppa-xenial.list.save
ubuntu-audio-dev-alsa-daily-trusty.list
ubuntu-audio-dev-alsa-daily-trusty.list.distUpgrade
ubuntu-audio-dev-alsa-daily-trusty.list.save
ubuntu-audio-dev-ppa-trusty.list
ubuntu-audio-dev-ppa-trusty.list.distUpgrade
ubuntu-audio-dev-ppa-trusty.list.save
ubuntuhandbook1-ubuntu-audacity-xenial.list
ubuntuhandbook1-ubuntu-audacity-xenial.list.save
ubuntu-mozilla-security-ppa-trusty.list
ubuntu-mozilla-security-ppa-trusty.list.distUpgrade
ubuntu-mozilla-security-ppa-trusty.list.save
ubuntu-sdk-team-ppa-trusty.list
ubuntu-sdk-team-ppa-trusty.list.distUpgrade
ubuntu-sdk-team-ppa-trusty.list.save
ubuntu-sdk-team-ubuntu-ppa-xenial.list
ubuntu-sdk-team-ubuntu-ppa-xenial.list.save
ubuntu-toolchain-r-ubuntu-test-xenial.list
ubuntu-toolchain-r-ubuntu-test-xenial.list.save
ubuntu-wine-ppa-trusty.list
ubuntu-wine-ppa-trusty.list.distUpgrade
ubuntu-wine-ppa-trusty.list.save
upubuntu-com-ubuntu-chat-xenial.list
upubuntu-com-ubuntu-chat-xenial.list.save
vala-team-ubuntu-ppa-xenial.list
vala-team-ubuntu-ppa-xenial.list.save
videolan-stable-daily-trusty.list
videolan-stable-daily-trusty.list.distUpgrade
videolan-stable-daily-trusty.list.save
videolan-ubuntu-stable-daily-xenial.list
videolan-ubuntu-stable-daily-xenial.list.save
vikoadi-ppa-trusty.list
vikoadi-ppa-trusty.list.distUpgrade
vikoadi-ppa-trusty.list.save
vikoadi-ubuntu-ppa-xenial.list
vikoadi-ubuntu-ppa-xenial.list.save
vivaldi.list
vivaldi.list.save
webupd8team-gthumb-trusty.list
webupd8team-gthumb-trusty.list.distUpgrade
webupd8team-gthumb-trusty.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.distUpgrade
webupd8team-java-trusty.list.save
webupd8team-pulseaudio-eq-trusty.list
webupd8team-pulseaudio-eq-trusty.list.distUpgrade
webupd8team-pulseaudio-eq-trusty.list.save
webupd8team-tribler-trusty.list
webupd8team-tribler-trusty.list.distUpgrade
webupd8team-tribler-trusty.list.save
webupd8team-ubuntu-java-xenial.list
webupd8team-ubuntu-java-xenial.list.save
webupd8team-ubuntu-rhythmbox-xenial.list
webupd8team-ubuntu-rhythmbox-xenial.list.save
webupd8team-ubuntu-y-ppa-manager-xenial.list
webupd8team-ubuntu-y-ppa-manager-xenial.list.save
webupd8team-y-ppa-manager-trusty.list
webupd8team-y-ppa-manager-trusty.list.distUpgrade
webupd8team-y-ppa-manager-trusty.list.save
whatsie.list
whatsie.list.save
xenial-partner.list
xenial-partner.list.save
yannubuntu-ubuntu-boot-repair-xenial.list
yannubuntu-ubuntu-boot-repair-xenial.list.save

```

---

### Post by westie457 on 2020-06-25
Probably the easiest way here is open 'Software & Updates' > 'Other Software' tab.
Look through the list and remove the check mark against all lines containing 'Trusty'.
When done click Close and reload the repository information.
Open a terminal```
sudo apt update #not strictly necessary but never hurts
sudo apt upgrade
```Post the results please.

With a lot of luck and keeping fingers crossed you might have a normal working system again.
If not the error messages might be different.

---

### Post by crazybear on 2020-06-29
I had long ago unchecked all sources that mentioned trusty!!!!!
I just ran your two lines, but no success. Thanks, but any other ideas?


```

$ sudo apt update #not strictly necessary but never hurts
Ign:1 http://dl.google.com/linux/earth/deb stable InRelease                    
Get:2 http://dl.google.com/linux/earth/deb stable Release [933 B]              
Err:3 http://dl.google.com/linux/earth/deb stable Release.gpg                  
  Bad header line Bad header data [IP: 172.217.23.206 80]
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]     
Hit:5 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:7 http://deb.opera.com/opera-developer stable InRelease [2,591 B]          
Ign:8 http://repo.vivaldi.com/stable/deb stable InRelease                      
Hit:9 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Ign:10 http://dl.bintray.com/aluxian/deb stable InRelease                      
Ign:11 http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu xenial InRelease     
Hit:12 http://repo.vivaldi.com/stable/deb stable Release                       
Err:13 http://dl.bintray.com/aluxian/deb stable Release                        
  404  Not Found [IP: 35.156.26.54 80]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]      
Ign:15 http://ppa.launchpad.net/abiword-stable/ppa/ubuntu xenial InRelease     
Get:16 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]    
Hit:17 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease    
Hit:18 http://ppa.launchpad.net/apandada1/typhoon/ubuntu xenial InRelease      
Err:7 http://deb.opera.com/opera-developer stable InRelease                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B8EC3BAABDC4346
Hit:19 https://repo.skype.com/deb stable InRelease                            
Hit:20 http://ppa.launchpad.net/audacity-team/daily/ubuntu xenial InRelease  
Hit:21 https://deb.torproject.org/torproject.org xenial InRelease            
Hit:22 https://brave-browser-apt-release.s3.brave.com xenial InRelease       
Ign:23 http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial InRelease     
Hit:24 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Ign:25 http://ppa.launchpad.net/do-core/ppa/ubuntu xenial InRelease          
Hit:27 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease
Hit:28 http://ppa.launchpad.net/fixnix/netspeed/ubuntu xenial InRelease       
Hit:30 http://ppa.launchpad.net/freecad-maintainers/freecad-daily/ubuntu xenial InRelease
Hit:31 http://ppa.launchpad.net/freetuxtv/freetuxtv-dev/ubuntu xenial InRelease
Hit:32 http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu xenial InRelease
Hit:33 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease        
Ign:34 https://packagecloud.io/Enrico204/Whatsapp-Desktop/debian stretch InRelease
Ign:35 http://ppa.launchpad.net/gnac-team/ppa/ubuntu xenial InRelease          
Hit:36 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease   
Ign:37 http://ppa.launchpad.net/heyarje/libav-11/ubuntu xenial InRelease       
Hit:38 http://ppa.launchpad.net/hsoft/ppa/ubuntu xenial InRelease              
Hit:39 http://ppa.launchpad.net/inameiname/stable/ubuntu xenial InRelease      
Hit:40 http://ppa.launchpad.net/jd-team/jdownloader/ubuntu xenial InRelease    
Ign:41 http://ppa.launchpad.net/jonathonf/vlc/ubuntu xenial InRelease
Ign:42 http://ppa.launchpad.net/libratbag-piper/piper-libratbag-git/ubuntu xenial InRelease
Ign:43 http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu xenial InRelease
Ign:44 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial InRelease
Hit:45 http://ppa.launchpad.net/linuxuprising/apps/ubuntu xenial InRelease     
Hit:46 http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu xenial InRelease    
Ign:47 http://ppa.launchpad.net/michael-gruz/canon/ubuntu xenial InRelease     
Err:29 https://riot.im/packages/debian xenial InRelease                        
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2850B265AC085BD
Hit:48 https://packagecloud.io/AllToMP3/alltomp3/ubuntu xenial InRelease
Ign:49 http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu xenial InRelease
Ign:50 http://ppa.launchpad.net/muravjov-il/ppa/ubuntu xenial InRelease
Err:51 https://packagecloud.io/Enrico204/Whatsapp-Desktop/debian stretch Release
  404  Not Found
Ign:52 http://ppa.launchpad.net/n-muench/calibre2/ubuntu xenial InRelease
Hit:53 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu xenial InRelease
Ign:54 http://ppa.launchpad.net/pascal-bach/unison/ubuntu xenial InRelease
Hit:55 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu xenial InRelease
Ign:56 http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial InRelease  
Hit:57 http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu xenial InRelease    
Hit:58 http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu xenial InRelease
Hit:59 http://ppa.launchpad.net/serge-rider/dbeaver-ce/ubuntu xenial InRelease 
Ign:60 http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu xenial InRelease
Ign:61 http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial InRelease     
Ign:62 http://ppa.launchpad.net/telepathy/ppa/ubuntu xenial InRelease          
Hit:63 http://ppa.launchpad.net/thierry-f/fork-michael-gruz/ubuntu xenial InRelease
Hit:64 http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu xenial InRelease
Hit:65 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu xenial InRelease
Hit:66 http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu xenial InRelease
Ign:67 http://ppa.launchpad.net/upubuntu-com/chat/ubuntu xenial InRelease      
Hit:68 http://ppa.launchpad.net/vala-team/ppa/ubuntu xenial InRelease
Ign:69 http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu xenial InRelease
Ign:70 http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu xenial InRelease
Hit:71 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease
Err:72 http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Err:73 http://ppa.launchpad.net/abiword-stable/ppa/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Err:74 http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial Release         
  404  Not Found [IP: 91.189.95.83 80]
Err:75 http://ppa.launchpad.net/do-core/ppa/ubuntu xenial Release              
  404  Not Found [IP: 91.189.95.83 80]
Err:76 http://ppa.launchpad.net/gnac-team/ppa/ubuntu xenial Release
  404  Not Found [IP: 91.189.95.83 80]
Err:77 http://ppa.launchpad.net/heyarje/libav-11/ubuntu xenial Release         
  404  Not Found [IP: 91.189.95.83 80]
Err:78 http://ppa.launchpad.net/jonathonf/vlc/ubuntu xenial Release            
  403  Forbidden [IP: 91.189.95.83 80]
Err:79 http://ppa.launchpad.net/libratbag-piper/piper-libratbag-git/ubuntu xenial Release
  404  Not Found [IP: 91.189.95.83 80]
Err:80 http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu xenial Release
  403  Forbidden [IP: 91.189.95.83 80]
Err:81 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release
  403  Forbidden [IP: 91.189.95.83 80]
Err:82 http://ppa.launchpad.net/michael-gruz/canon/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Err:83 http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu xenial Release   
  404  Not Found [IP: 91.189.95.83 80]
Err:84 http://ppa.launchpad.net/muravjov-il/ppa/ubuntu xenial Release          
  404  Not Found [IP: 91.189.95.83 80]
Err:85 http://ppa.launchpad.net/n-muench/calibre2/ubuntu xenial Release        
  404  Not Found [IP: 91.189.95.83 80]
Err:86 http://ppa.launchpad.net/pascal-bach/unison/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Err:87 http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial Release    
  404  Not Found [IP: 91.189.95.83 80]
Err:88 http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu xenial Release
  404  Not Found [IP: 91.189.95.83 80]
Err:89 http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Err:90 http://ppa.launchpad.net/telepathy/ppa/ubuntu xenial Release            
  404  Not Found [IP: 91.189.95.83 80]
Err:91 http://ppa.launchpad.net/upubuntu-com/chat/ubuntu xenial Release        
  404  Not Found [IP: 91.189.95.83 80]
Err:92 http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu xenial Release
  404  Not Found [IP: 91.189.95.83 80]
Err:93 http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu xenial Release    
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                                                  
E: The repository 'http://dl.google.com/linux/earth/deb stable Release' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://dl.bintray.com/aluxian/deb stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com/opera-developer stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B8EC3BAABDC4346
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://riot.im/packages/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2850B265AC085BD
E: The repository 'https://packagecloud.io/Enrico204/Whatsapp-Desktop/debian stretch Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/abiword-stable/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/do-core/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/gnac-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/heyarje/libav-11/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/jonathonf/vlc/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/libratbag-piper/piper-libratbag-git/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-3-5/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/michael-gruz/canon/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/muravjov-il/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/n-muench/calibre2/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/pascal-bach/unison/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/telepathy/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/upubuntu-com/chat/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
peter-and-crazybear@peterandcrazybear-GA-X58A-UD7:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.54-1ubuntu1) but 1.2.54-1ubuntu1.1 is installed
 libpng12-0:i386 : Breaks: libpng12-0 (!= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
 libpng12-dev : Depends: libpng12-0 (= 1.2.54-1ubuntu1.1) but 1.2.54-1ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by webaake on 2020-06-29
Yes, try ```
dpkg -r --force-depends 'PACKAGE_NAME"
```

--force-depends turn stops into warnings instead, and removes the package.

Also I suspect your Debian repo in the sources.list file. Since the error message refers to the Debian Change log. Try to disable that Debian repo. Debian and Ubuntu is a dangerous mix since they are too alike, in a way.

---

### Post by ajgreeny on 2020-06-29
And even having removed all those sources.list.d entries from the system I don't  think I've  ever seen quite such a long list of added repos.

Problems such as you've  seen are much more likely, or even probable if you complicate sources as much as you seem to have done, so in future proceed with a bit more caution  before adding too many third party repos.

---

### Post by Impavidus on 2020-06-29
Your system is held together with strings and tape.

You've got about 75 PPAs, which is insane and likely to cause trouble. About 25 of those don't provide software for Xenial. They should be removed, along with the software you got from those PPAs. You've mixed 32 and 64 bit packages, which is allowed, but I would avoid it. Your release is getting close to end of life.

My solution: wipe your hard drive and make a fresh start with 20.04. Then try to keep it clean.

---

### Post by crazybear on 2020-07-02
> **webaake said:**
> Yes, try ```
dpkg -r --force-depends 'PACKAGE_NAME"
```

--force-depends turn stops into warnings instead, and removes the package.

Also I suspect your Debian repo in the sources.list file. Since the error message refers to the Debian Change log. Try to disable that Debian repo. Debian and Ubuntu is a dangerous mix since they are too alike, in a way.


Sorry, this doesn't make sense to me as to what you are suggesting....that I do that with one of the libpng packages? I also don't understand what  you suggest about the  'disabling the Debian repo'. Please clarify.

---

### Post by crazybear on 2020-07-02
> **Impavidus said:**
> Your system is held together with strings and tape.

You've got about 75 PPAs, which is insane and likely to cause trouble. About 25 of those don't provide software for Xenial. They should be removed, along with the software you got from those PPAs. You've mixed 32 and 64 bit packages, which is allowed, but I would avoid it. Your release is getting close to end of life.

My solution: wipe your hard drive and make a fresh start with 20.04. Then try to keep it clean.

At the moment, my entire life and if it continues many more weeks or months is held together by string and tape and a lot of lawyers and my own legal moves and preparation for a period of homelessness and other things I can't go into........ I need to take a conservative route with this system for now......just no other option....in the late Fall or Winter, if I'm lucky and still alive, I can do something like that. My life is less stable than my system....

Your suggestion is not going to be possible. I'm being evicted soon and  am in a HUGE legal battle. I'll probably be homeless for some months and  lucky if I land homefull again. I'm 70, have cancer, am living in a  foreign country I don't much like, can not live in my own country  because of being a whistleblower and it is too dangerous, did not make  any money this year due to the virus pandemic and the legal  mess......I'm stuck with what i have for now. I can NOT try normal  things......more I don't want to go into....be lucky you have normal  lives. I don't right now. I can't make any major changes just now until  my life is stable again....at minimum many months and legal battles  away. Life can be complicated (if you try to tell the truth [WARNING!]) - even more than my package list.                 Sorry, my life is at the survival level and minimal 'keeping the system going' is what I have to do now

...in fact, my 'real computer system/HDDs' are now illegally seized, and I'm battling to get it back in Court battles. I need the  simplest solution, not the most radical - even if it is the 'best'...for me it is to dangerous to attempt now....especially NOW!

Is there not just a way to delete with one command all trusty ppa's? I'm also confused by the apparent multiple lists.

---

### Post by webaake on 2020-07-02
Seems your best bet is to reinstall.

---

### Post by crazybear on 2020-07-04
Maybe I'm not so 'crazy' and ONLY held together by tape as has been so far theorized.....

libpng12-0 1.2.50-2+deb8u3
```

Thank you for taking the time to report this bug and trying to help make
Ubuntu better. However, [U][B]it seems that you are not using a software
package provided by the official Ubuntu repositories[/B][/U]. Because of this
the Ubuntu project can not support or fix your particular bug. Please
report this bug to the provider of the software package. Thanks!

If you are interested in learning more about software repositories and
Ubuntu, check [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories).

** Changed in: libpng (Ubuntu)
       Status: Confirmed => Invalid

-- 
You received this bug notification because you are subscribed to the bug
report.
[https://bugs.launchpad.net/bugs/1765649](https://bugs.launchpad.net/bugs/1765649)

Title:
  package libpng12-0 1.2.54-1ubuntu1 [modified:
  usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG
  usr/share/doc/libpng12-0/README.gz
  usr/share/doc/libpng12-0/changelog.Debian.gz] failed to
  install/upgrade: trying to overwrite shared
  '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other
  instances of package libpng12-0:i386

Status in libpng package in Ubuntu:
  Invalid

Bug description:
  This bug appeared when I was trying to install teamviewer which doesn't work.
  There are some dependencies that break the installation.
  Then I tried to remove teamviewer:
  sudo apt-get remove teamviewer
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  You might want to run 'apt-get -f install' to correct these:
  The following packages have unmet dependencies:
   libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.54-1ubuntu1) but 1.2.50-2+deb8u3 is to be installed
   libpng12-0:i386 : Depends: libc6:i386 (>= 2.11) but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Breaks: libpng12-0 (!= 1.2.50-2+deb8u3) but 1.2.54-1ubuntu1 is to be installed
  E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

  Then as suggested I tried: sudo apt-get -f install 
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Correcting dependencies... Done
  The following additional packages will be installed:
    gcc-6-base:i386 libc6:i386 libgcc1:i386 libpng12-0:i386 zlib1g:i386
  Suggested packages:
    glibc-doc:i386 locales:i386
  The following packages will be REMOVED:
    teamviewer
  The following NEW packages will be installed:
    gcc-6-base:i386 libc6:i386 libgcc1:i386 zlib1g:i386
  The following packages will be upgraded:
    libpng12-0:i386
  1 upgraded, 4 newly installed, 1 to remove and 210 not upgraded.
  3 not fully installed or removed.
  Need to get 2.501 kB of archives.
  After this operation, 142 MB disk space will be freed.
  Do you want to continue? [Y/n] y
  Get:1 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 gcc-6-base i386 6.0.1-0ubuntu1 [14,3 kB]
  Get:2 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 libgcc1 i386 1:6.0.1-0ubuntu1 [46,8 kB]
  Get:3 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libc6 i386 2.23-0ubuntu10 [2.266 kB]
  Get:4 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial-updates/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4.1 [52,1 kB]
  Get:5 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 libpng12-0 i386 1.2.54-1ubuntu1 [122 kB]
  Fetched 2.501 kB in 0s (4.625 kB/s)       
  Preconfiguring packages ...
  (Reading database ... 253717 files and directories currently installed.)
  Removing teamviewer (12.0.93330) ...
  Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
  Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
  Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
  Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
  Rebuilding /usr/share/applications/bamf-2.index...
  Processing triggers for mime-support (3.59ubuntu1) ...
  (Reading database ... 253416 files and directories currently installed.)
  Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
  Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
  dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
   trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  Selecting previously unselected package gcc-6-base:i386.
  Preparing to unpack .../gcc-6-base_6.0.1-0ubuntu1_i386.deb ...
  Unpacking gcc-6-base:i386 (6.0.1-0ubuntu1) ...
  Selecting previously unselected package libgcc1:i386.
  Preparing to unpack .../libgcc1_1%3a6.0.1-0ubuntu1_i386.deb ...
  Unpacking libgcc1:i386 (1:6.0.1-0ubuntu1) ...
  Selecting previously unselected package libc6:i386.
  Preparing to unpack .../libc6_2.23-0ubuntu10_i386.deb ...
  Unpacking libc6:i386 (2.23-0ubuntu10) ...
  Replacing files in old package libc6-i386 (2.23-0ubuntu10) ...
  Selecting previously unselected package zlib1g:i386.
  Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_i386.deb ...
  Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4.1) ...
  Processing triggers for libc-bin (2.23-0ubuntu10) ...
  Errors were encountered while processing:
   /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb
  E: Sub-process /usr/bin/dpkg returned an error code (1)

  ProblemType: Package
  DistroRelease: Ubuntu 16.04
  Package: libpng12-0 1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz]
  ProcVersionSignature: Ubuntu 4.13.0-38.43~16.04.1-generic 4.13.16
  Uname: Linux 4.13.0-38-generic x86_64
  NonfreeKernelModules: nvidia_uvm nvidia_drm nvidia_modeset nvidia
  ApportVersion: 2.20.1-0ubuntu2.15
  Architecture: amd64
  Date: Fri Apr 20 12:30:39 2018
  Dependencies:
   gcc-6-base 6.0.1-0ubuntu1
   libc6 2.23-0ubuntu10
   libgcc1 1:6.0.1-0ubuntu1
   zlib1g 1:1.2.8.dfsg-2ubuntu4.1
  DpkgTerminalLog:
   Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
   Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
   dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
    trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  DuplicateSignature:
   package:libpng12-0:1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz]
   Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
   dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
    trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  ErrorMessage: trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  InstallationDate: Installed on 2017-10-21 (181 days ago)
  InstallationMedia: Ubuntu 16.04.3 LTS "Xenial Xerus" - Release amd64 (20170801)
  RelatedPackageVersions:
   dpkg 1.18.4ubuntu1.2
   apt  1.2.24
  SourcePackage: libpng
  Title: package libpng12-0 1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz] failed to install/upgrade: trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  UpgradeStatus: No upgrade log present (probably fresh install)

To manage notifications about this bug go to:
[https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1765649/+subscriptions](https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1765649/+subscriptions)

```

---

### Post by crazybear on 2020-07-04
> **webaake said:**
> Seems your best bet is to reinstall.

reinstall what?! reinstall libpng is impossible. reinstall my entire Ubuntu version or an updated one - _**maybe**_ in half a year...I'll be homeless from a few weeks from now until then..and no assurance of even being alive at that end of half a year.

I need quick, easy solutions - NOT the best, ideal, solutions one would do if one had a stable life, stable system, stable living situation, stable income, stable roof over ones head and even some reasonable expectation to be alive in the near future. Sorry to sound upset, I understand that by definition most people have average lives. Sadly, I do not and have not for 30 ***ing years and I'm very tired of it to tell the truth. I'm hanging on to life by my fingernails. My computer and access to the internet is essential only after keeping alive. I need conservative solutions at this point in time. Pardon my emotion. I'm emotional. Someone just killed my dog and the closest and only close living being to me........

---

### Post by webaake on 2020-07-04
Then; dpkg -r --force-depends .....

Catch 22 I'd guess...

---

### Post by crazybear on 2020-07-05
Can anyone translate into which package or repository they mean, below, when they state "[U][B]it seems that you are not using a software
package provided by the official Ubuntu repositories" I don't understand what they mean. Where does the 'official' libpng come from - or is it everywhere broken?[/B][/U]

> **crazybear said:**
> Maybe I'm not so 'crazy' and ONLY held together by tape as has been so far theorized.....

libpng12-0 1.2.50-2+deb8u3
```

Thank you for taking the time to report this bug and trying to help make
Ubuntu better. However, [U][B]it seems that you are not using a software
package provided by the official Ubuntu repositories[/B][/U]. Because of this
the Ubuntu project can not support or fix your particular bug. Please
report this bug to the provider of the software package. Thanks!

If you are interested in learning more about software repositories and
Ubuntu, check [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories).

** Changed in: libpng (Ubuntu)
       Status: Confirmed => Invalid

-- 
You received this bug notification because you are subscribed to the bug
report.
[https://bugs.launchpad.net/bugs/1765649](https://bugs.launchpad.net/bugs/1765649)

Title:
  package libpng12-0 1.2.54-1ubuntu1 [modified:
  usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG
  usr/share/doc/libpng12-0/README.gz
  usr/share/doc/libpng12-0/changelog.Debian.gz] failed to
  install/upgrade: trying to overwrite shared
  '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other
  instances of package libpng12-0:i386

Status in libpng package in Ubuntu:
  Invalid

Bug description:
  This bug appeared when I was trying to install teamviewer which doesn't work.
  There are some dependencies that break the installation.
  Then I tried to remove teamviewer:
  sudo apt-get remove teamviewer
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  You might want to run 'apt-get -f install' to correct these:
  The following packages have unmet dependencies:
   libpng12-0 : Breaks: libpng12-0:i386 (!= 1.2.54-1ubuntu1) but 1.2.50-2+deb8u3 is to be installed
   libpng12-0:i386 : Depends: libc6:i386 (>= 2.11) but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Breaks: libpng12-0 (!= 1.2.50-2+deb8u3) but 1.2.54-1ubuntu1 is to be installed
  E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

  Then as suggested I tried: sudo apt-get -f install 
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Correcting dependencies... Done
  The following additional packages will be installed:
    gcc-6-base:i386 libc6:i386 libgcc1:i386 libpng12-0:i386 zlib1g:i386
  Suggested packages:
    glibc-doc:i386 locales:i386
  The following packages will be REMOVED:
    teamviewer
  The following NEW packages will be installed:
    gcc-6-base:i386 libc6:i386 libgcc1:i386 zlib1g:i386
  The following packages will be upgraded:
    libpng12-0:i386
  1 upgraded, 4 newly installed, 1 to remove and 210 not upgraded.
  3 not fully installed or removed.
  Need to get 2.501 kB of archives.
  After this operation, 142 MB disk space will be freed.
  Do you want to continue? [Y/n] y
  Get:1 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 gcc-6-base i386 6.0.1-0ubuntu1 [14,3 kB]
  Get:2 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 libgcc1 i386 1:6.0.1-0ubuntu1 [46,8 kB]
  Get:3 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libc6 i386 2.23-0ubuntu10 [2.266 kB]
  Get:4 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial-updates/main i386 zlib1g i386 1:1.2.8.dfsg-2ubuntu4.1 [52,1 kB]
  Get:5 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) xenial/main i386 libpng12-0 i386 1.2.54-1ubuntu1 [122 kB]
  Fetched 2.501 kB in 0s (4.625 kB/s)       
  Preconfiguring packages ...
  (Reading database ... 253717 files and directories currently installed.)
  Removing teamviewer (12.0.93330) ...
  Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
  Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
  Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
  Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
  Rebuilding /usr/share/applications/bamf-2.index...
  Processing triggers for mime-support (3.59ubuntu1) ...
  (Reading database ... 253416 files and directories currently installed.)
  Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
  Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
  dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
   trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  Selecting previously unselected package gcc-6-base:i386.
  Preparing to unpack .../gcc-6-base_6.0.1-0ubuntu1_i386.deb ...
  Unpacking gcc-6-base:i386 (6.0.1-0ubuntu1) ...
  Selecting previously unselected package libgcc1:i386.
  Preparing to unpack .../libgcc1_1%3a6.0.1-0ubuntu1_i386.deb ...
  Unpacking libgcc1:i386 (1:6.0.1-0ubuntu1) ...
  Selecting previously unselected package libc6:i386.
  Preparing to unpack .../libc6_2.23-0ubuntu10_i386.deb ...
  Unpacking libc6:i386 (2.23-0ubuntu10) ...
  Replacing files in old package libc6-i386 (2.23-0ubuntu10) ...
  Selecting previously unselected package zlib1g:i386.
  Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_i386.deb ...
  Unpacking zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4.1) ...
  Processing triggers for libc-bin (2.23-0ubuntu10) ...
  Errors were encountered while processing:
   /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb
  E: Sub-process /usr/bin/dpkg returned an error code (1)

  ProblemType: Package
  DistroRelease: Ubuntu 16.04
  Package: libpng12-0 1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz]
  ProcVersionSignature: Ubuntu 4.13.0-38.43~16.04.1-generic 4.13.16
  Uname: Linux 4.13.0-38-generic x86_64
  NonfreeKernelModules: nvidia_uvm nvidia_drm nvidia_modeset nvidia
  ApportVersion: 2.20.1-0ubuntu2.15
  Architecture: amd64
  Date: Fri Apr 20 12:30:39 2018
  Dependencies:
   gcc-6-base 6.0.1-0ubuntu1
   libc6 2.23-0ubuntu10
   libgcc1 1:6.0.1-0ubuntu1
   zlib1g 1:1.2.8.dfsg-2ubuntu4.1
  DpkgTerminalLog:
   Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
   Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
   dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
    trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  DuplicateSignature:
   package:libpng12-0:1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz]
   Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) over (1.2.50-2+deb8u3) ...
   dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb (--unpack):
    trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  ErrorMessage: trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  InstallationDate: Installed on 2017-10-21 (181 days ago)
  InstallationMedia: Ubuntu 16.04.3 LTS "Xenial Xerus" - Release amd64 (20170801)
  RelatedPackageVersions:
   dpkg 1.18.4ubuntu1.2
   apt  1.2.24
  SourcePackage: libpng
  Title: package libpng12-0 1.2.54-1ubuntu1 [modified: usr/share/doc/libpng12-0/ANNOUNCE usr/share/doc/libpng12-0/KNOWNBUG usr/share/doc/libpng12-0/README.gz usr/share/doc/libpng12-0/changelog.Debian.gz] failed to install/upgrade: trying to overwrite shared '/usr/share/doc/libpng12-0/KNOWNBUG', which is different from other instances of package libpng12-0:i386
  UpgradeStatus: No upgrade log present (probably fresh install)

To manage notifications about this bug go to:
[https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1765649/+subscriptions](https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1765649/+subscriptions)

```

---

### Post by crazybear on 2020-07-05
> **webaake said:**
> Then; dpkg -r --force-depends .....

Catch 22 I'd guess...

As stated earlier, this does not work..... can't be forced. Can't be removed. Stuck.

---

### Post by Impavidus on 2020-07-05
A fresh install of Ubuntu is the quick and easy solution. It takes about an hour (a bit more if you have to download the live disk over a slow connection). You will loose some arcane software, but a system that just works is incompatible with having arcane software. If you really want software that hasn't been built for your version of Ubuntu, you have to jump through some hoops. It's not easy.

Your problem is caused by having two incompatible versions of the same package, one 32 bit, the other 64 bit. It's supposed to be possible to have both the 32 bit and the 64 bit version of a library installed at the same time, but when only using software from the official sources there should never be a need to do so.

If I were to attempt to fix this, my approach would be to remove every package depending on the 32 bit libpng, then the 32 bit libpng itself, then upgrade the 64 bit libpng, then reinstall the removed packages. But I wouldn't attempt to fix it; I would perform a fresh install.

---

### Post by crazybear on 2020-07-09
> **Impavidus said:**
> A fresh install of Ubuntu is the quick and easy solution. It takes about an hour (a bit more if you have to download the live disk over a slow connection). You will loose some arcane software, but a system that just works is incompatible with having arcane software. If you really want software that hasn't been built for your version of Ubuntu, you have to jump through some hoops. It's not easy.

Your problem is caused by having two incompatible versions of the same package, one 32 bit, the other 64 bit. It's supposed to be possible to have both the 32 bit and the 64 bit version of a library installed at the same time, but when only using software from the official sources there should never be a need to do so.

If I were to attempt to fix this, my approach would be to remove every package depending on the 32 bit libpng, then the 32 bit libpng itself, then upgrade the 64 bit libpng, then reinstall the removed packages. But I wouldn't attempt to fix it; I would perform a fresh install.

I would just love to remove all 32 bit packages...but the computer will not allow [I can't make it!]. If you can tell me how to do so, please do! This 'it only takes an hour' doesn't cut it for me. Everytime I have tried to upgrade it was days or weeks of struggle and then I had two computers - so I always had one to be online for help with. Now, the other computer is seized [as is most of my life]....too complex to go into and doesn't apply here. My life is not normal and I'm going to have to move from where I am now in an unknown but few days...I must wait until my life is stable to even think of installing 20.04. The problems of bringing over all the programs I want, making it Gnome desktop and looking as I am used to, making it work with some older hardware and some other factors is just too risky now. I appreciate the 'suggestion' and it is logical for someone with a normal life. I am not such a person. I'm on the move, involuntarily, for being a whistleblower. While I have never looked at these packages before, they must have been there for years. Why all of a sudden are these three conflicting with one another and I see [posted above] this is a known bug, but nothing has yet been done with it. When I next get money, I will get a laptop - have only this too large desktop and intstall on it a new 20.04...not before then and some stability where I don't have to be packed and ready to move on 48 hr. notice.

N.B. Here is the bug - there are several variants of it online: [https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1799215](https://bugs.launchpad.net/ubuntu/+source/libpng/+bug/1799215)

---

### Post by Impavidus on 2020-07-10
Yesterday there was another thread with a similar problem ([https://ubuntuforums.org/showthread.php?t=2446898](https://ubuntuforums.org/showthread.php?t=2446898)), this time with libjpeg-turbo8. The problem isn't actually with libpng, but with the way apt handles upgrades of packages that are installed in two different architectures.

Still, I stand by my suggestion. A fresh install is the quick and simple solution. If the simplest solution is too complex, there is no solution. Sorry.

Last Sunday I installed Xubuntu 20.04. I booted the live disk at 19:15, changed some partitions, installed and was running the new system at 20:00. Installing Ubuntu is simpler than fixing it, yet you want to fix it because installing is too complex. That doesn't add up.

---

### Post by crazybear on 2020-07-11
> **Impavidus said:**
> Yesterday there was another thread with a similar problem ([https://ubuntuforums.org/showthread.php?t=2446898](https://ubuntuforums.org/showthread.php?t=2446898)), this time with libjpeg-turbo8. The problem isn't actually with libpng, but with the way apt handles upgrades of packages that are installed in two different architectures.

Still, I stand by my suggestion. A fresh install is the quick and simple solution. If the simplest solution is too complex, there is no solution. Sorry.

Last Sunday I installed Xubuntu 20.04. I booted the live disk at 19:15, changed some partitions, installed and was running the new system at 20:00. Installing Ubuntu is simpler than fixing it, yet you want to fix it because installing is too complex. That doesn't add up.

You can not see the World from another person's point of view - only your own. Your 'solution/suggestion' is right for you [and perhaps many others]; but too dangerous and problematic for me now. Yes, for now I want to fix this install. I don't want to list why for me your solution is dangerous for me - it just is - I know from the past and then as I said I had another computer. Now, I only have one and if it gets messed up, I'll not even be able to get online for help...nor do I have the time. I could have to move [to homelessness, or a perhaps a place with no internet at best] at any moment without much warning. You just refuse to get it - how it is for me. I have many programs other than those that come with a normal distribution and need to make many changes after. I've always had great problems with a new install and won't chance it now. It does add up and you'r wasting both of our times in discussing it. Many people just install a new version and use it with very little additional done. I must do a huge amount of changes and adding both programs/changes and data. Last time was a week long nightmare and my life was not at the brink as now. You'll not convince me to take this risk at this point. If anyone knows a way to fix my system to limp along until my life is somewhat secure, I'd appreciate it. If not, the system is still working, but I can't update some programs and packages and will just have to live with that for now. I spend all day every day writing legal briefs and doing emergency things. I can NOT afford my system down for a day or a week...it would literally kill me. Thanks, but no thanks. My situation is unusual..but it is what it is.

---

### Post by Jan_Johansson on 2021-03-20
Crazybear, open a terminal and type this:

sudo dpkg -r --force-depends libpng12-0:i386

then wait for prompt and then type: 

sudo apt-get update

wait for prompt and then type:

sudo apt-get upgrade

Open synaptics and click fix broken packages and you should be ok now, I just performed this after having same issue as you(in my case I followed the instructions here [https://vitux.com/how-to-edit-pdf-files-in-ubuntu/](https://vitux.com/how-to-edit-pdf-files-in-ubuntu/)  from Karim Buzdar on how to install PDF Editor, and that caused my problem). And I also run 16.04 and will not upgrade until 20.04.1 is out and working as it should(i know its out but many people have reported that many things are not working).


Hope this helped you

Jan

On a sidenote: I seriously don't understand why we in 2021, still have  to wipe our installation and install a fresh one to get a newer system -  even android can figure out to do upgrades without having to start  over, so why can't Ubuntu figure that one out???

---

