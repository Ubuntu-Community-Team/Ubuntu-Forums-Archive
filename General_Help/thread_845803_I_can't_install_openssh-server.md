---
title: "I can't install openssh-server"
date: 2008-06-30
forum: General Help
---

### Post by spintriae on 2008-06-30
Please tell me what's going on and how to correct it. 

```
sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ssh-askpass rssh molly-guard
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/248kB of archives.
After unpacking 655kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.6p1-5build1_i386.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.6p1-5build1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by markekeller on 2008-07-01
Hmm!  Do you have [FONT="Monospace"]laptop-detect, xfce4-verve-plugin, python-gnuginterface,[/FONT] and [FONT="Monospace"]hal-info[/FONT] installed already?  There's obviously some corruption going on.  If those packages are installed, try
```

apt-get --reinstall install <packagename>
```
for each of them, and [FONT="Monospace"]zlib1g[/FONT], too.  And if that doesn't solve your problems, try
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get dist-upgrade
```
and if any of them return errors, post the contents of /etc/apt/sources.list here.

---

### Post by spintriae on 2008-07-01
Those packages are already installed. I'll try to reinstall them. 

How do I go about checking for corruption? I tried

```
sudo shutdown -F -r now
```

and it restarted normally.

---

### Post by spintriae on 2008-07-01
Results of the reinstalls (pretty redundent):
```
kc@leonardo:~$ sudo apt-get --reinstall install laptop-detect
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/4898B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/laptop-detect_0.13.2ubuntu1_i386.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/laptop-detect_0.13.2ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
kc@leonardo:~$ sudo apt-get --reinstall install python-gnupginterface
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 21.0kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com gutsy/main python-gnupginterface 0.3.2-9ubuntu1 [21.0kB]
Fetched 21.0kB in 0s (24.5kB/s)            
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/python-gnupginterface_0.3.2-9ubuntu1_all.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnupginterface_0.3.2-9ubuntu1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
kc@leonardo:~$ sudo apt-get --reinstall install hal-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 41.5kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com gutsy/main hal-info 20070618-1ubuntu3 [41.5kB]
Fetched 41.5kB in 1s (35.7kB/s)  
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/hal-info_20070618-1ubuntu3_all.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/hal-info_20070618-1ubuntu3_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
kc@leonardo:~$ sudo apt-get --reinstall install zlib1g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 73.0kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com gutsy/main zlib1g 1:1.2.3.3.dfsg-5ubuntu2 [73.0kB]
Fetched 73.0kB in 1s (52.5kB/s)
(Reading database ... 
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfce4-verve-plugin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hal-info' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/zlib1g_1%3a1.2.3.3.dfsg-5ubuntu2_i386.deb (--unpack):
 files list file for package `zlib1g' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/zlib1g_1%3a1.2.3.3.dfsg-5ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
kc@leonardo:~$ sudo apt-get clean all
kc@leonardo:~$ sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]  
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Hit http://archive.ubuntu.com gutsy Release          
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
kc@leonardo:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

/etc/apt/sources.list:
```
kc@leonardo:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by markekeller on 2008-07-01
One way to look for corruption would be to examine [FONT="Monospace"]/var/lib/dpkg/info/<package name>.list[/FONT] for each of the packages in question, and see if they look damaged somehow (compare them to the files for healthy packages).

And your sources.list looks damaged; all those 'Line commented out' messages!  Try uncommenting them.

---

### Post by soccerboy on 2008-07-01
> **markekeller said:**
> Hmm!  Do you have [FONT="Monospace"]laptop-detect, xfce4-verve-plugin, python-gnuginterface,[/FONT] and [FONT="Monospace"]hal-info[/FONT] installed already?  There's obviously some corruption going on.  If those packages are installed, try
```

apt-get --reinstall install <packagename>
```
for each of them, and [FONT="Monospace"]zlib1g[/FONT], too.  And if that doesn't solve your problems, try
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get dist-upgrade
```
and if any of them return errors, post the contents of /etc/apt/sources.list here.

maybe use ```
sudo apt-get -f install openssh-server
```

EDIT: It doesn't look like you have any repos enabled.  I'd ask for a new sources.list file from someone with Xubuntu 7.10.

---

