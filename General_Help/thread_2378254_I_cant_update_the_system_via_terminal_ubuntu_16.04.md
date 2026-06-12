---
title: "I cant update the system via terminal ubuntu 16.04 32bit"
date: 2017-11-21
forum: General Help
---

### Post by eagleftvp-co on 2017-11-21
Hi try to update the system ubuntu 16.04 32 bit via Terminal and get  this message..:
```
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: The repository 'http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial Release' does not have a Release file.
W: The repository 'http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial Release' does not have a Release file.
E: Failed to fetch [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
```
Warning:  apt-get update failed for some reason

---

### Post by deadflowr on 2017-11-21
Per the Errors, there are no archives for xenial (16.04) for ether the pinta-maintainers ppa or the skunk/pepper ppa.
So remove those
```
sudo add-apt-repository -r ppa:skunk/pepper-flash
sudo add-apt-repository -r ppa:pinta-maintainers/pinta-stable
```

As for the warnings you have the same lines repeated in your sources.list file.
lines 36, 38, and 39 seem to be the same as line 57.
You'll need to remove all but one of those lines.
Post the sources.list if you need help figuring that out
```
cat /etc/apt/sources.list
```

Also please read the skunk/pepper home page for how to install pepper flash:
[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash]("https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash")

---

### Post by eagleftvp-co on 2017-11-21
eagle@eagle:~$ cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial main universe multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates main' main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates main universe multiverse restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-backports main' universe main multiverse restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main universe multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-proposed restricted main universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-proposed restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main main'
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main'
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main
# deb [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main' universe main multiverse restricted
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
eagle@eagle:~$
```

---

### Post by deadflowr on 2017-11-21
Seems the issue with the sources.list is line 57 so add a comment (the # symbol) to that one and see if that fixes the Warnings issue.
run
```
sudo nano /etc/apt/sources.list
```
and change the line (should be the 3rd to last line) from
```
deb http://security.ubuntu.com/ubuntu/ xenial-security main' universe main multiverse restricted
```
to 
```
# deb http://security.ubuntu.com/ubuntu/ xenial-security main' universe main multiverse restricted
```

this will comment out the line making apt ignore it.
then press ctrl + X > then press Y to accept the changes and then press enter to save and exit nano.
If all's well try an apt-get update and see if the errors and warnings persist.

---

### Post by eagleftvp-co on 2017-11-21
thank you for your help ..i try to update but i have the same errors and warnings 

```
eagle@eagle:~$ sudo apt-get update
[sudo] password for eagle: 
Hit:1 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Hit:5 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial-proposed InRelease            
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Ign:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:10 [http://ppa.launchpad.net/costales/folder-color/ubuntu](http://ppa.launchpad.net/costales/folder-color/ubuntu) xenial InRelease  
Hit:11 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease  
Hit:13 [http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu) xenial InRelease
Hit:14 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) xenial InRelease
Fetched 102 kB in 1s (81,9 kB/s)
Reading package lists... Done
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main'/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Packages (main'/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Translations (main'/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Translations (main'/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target DEP-11 (main'/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main'/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (main'/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Packages (main'/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Translations (main'/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Translations (main'/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target DEP-11 (main'/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main'/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:57
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:57
W: Target Packages (main'/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Packages (main'/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Translations (main'/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Translations (main'/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target DEP-11 (main'/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main'/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:62
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:62
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:62
W: Target Packages (main'/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Packages (main'/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Translations (main'/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Translations (main'/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target DEP-11 (main'/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main'/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:65
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:65
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list:65
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:65
eagle@eagle:~$
```

---

### Post by deadflowr on 2017-11-21
What does the sources.list file say now?

---

### Post by eagleftvp-co on 2017-11-22
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted #Added by software-properties
 
 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
 # newer versions of the distribution.
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial main restricted
 deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial main universe multiverse restricted #Added by software-properties
 
 
 ## Major bug fix updates produced after the final release of the
 ## distribution.
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates main' main restricted
 deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates main universe multiverse restricted #Added by software-properties
 
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team. Also, please note that software in universe WILL NOT receive any
 ## review or updates from the Ubuntu security team.
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial universe
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates universe
 
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu
 ## security team.
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial multiverse
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
 
 
 ## N.B. software from this repository may not have been tested as
 ## extensively as that contained in the main release, although it includes
 ## newer versions of some applications which may provide useful features.
 ## Also, please note that software in backports WILL NOT receive any review
 ## or updates from the Ubuntu security team.
 deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-backports main' universe main multiverse restricted
 deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse #Added by software-properties
 
 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main universe multiverse restricted #Added by software-properties
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
 
 
 ## Uncomment the following two lines to add software from Canonical's
 ## 'partner' repository.
 ## This software is not part of Ubuntu, but is offered by Canonical and the
 ## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

---

