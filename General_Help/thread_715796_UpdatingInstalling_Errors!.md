---
title: "Updating/Installing Errors!"
date: 2008-03-05
forum: General Help
---

### Post by badboyz107 on 2008-03-05
I can not update ANYTHING by using sudo etc etc etc I usually get to the part were it gets packages but then it chokes and says that there are to many errors...I'll post a copy of trying to install automatix2 here and see what you guys can come up with.....keep in mind this same type of error happens all the time, regardless of what I am trying to install or update.

I'm using my Ubuntu machine cause my window$ puter died (congestive processor failure me thinks!)

#@troy-desktop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
Password:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
#@troy-desktop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--07:36:36--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key.1'
Resolving [www.getautomatix.com](www.getautomatix.com)... 64.69.36.51
Connecting to www.getautomatix.com|64.69.36.51|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s             

07:36:36 (69.02 MB/s) - `automatix2.key.1' saved [1706/1706]

#@troy-desktop:~$ gpg --import automatix2.key
gpg: key E23C5FC3: "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
#@troy-desktop:~$ gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
#@troy-desktop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Fetched 5B in 1s (3B/s)  
Reading package lists... Done
#@troy-desktop:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python2.4 python2.4-minimal
Suggested packages:
  python2.4-doc python-profiler
The following NEW packages will be installed:
  automatix2 python2.4 python2.4-minimal
0 upgraded, 3 newly installed, 0 to remove and 9 not upgraded.
Need to get 4024kB of archives.
After unpacking 12.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main automatix2 1.1-4.13-7.04feisty_i386 [257kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main python2.4-minimal 2.4.4-2ubuntu7 [970kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main python2.4 2.4.4-2ubuntu7 [2797kB]
Fetched 4024kB in 34s (117kB/s)                                                
Selecting previously deselected package python2.4-minimal.
(Reading database ... dpkg: error processing /var/cache/apt/archives/python2.4-minimal_2.4.4-2ubuntu7_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `linux-headers-2.6.20-16': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-minimal_2.4.4-2ubuntu7_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2008-03-05
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

p.s.  Not sure why you even bother to install automatix2?  You just compound your problems with it.

---

### Post by badboyz107 on 2008-03-05
Well I didn't necessarily know that it was so bad, cause I have NO idea what I'm doing really....enough to break this machine as well I suppose, but the error occurs no matter what I try to do....couldnt even turn on the Numlock at bootup!

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by badboyz107 on 2008-03-06
No suggestions??  Anyone??

---

### Post by kesman on 2008-03-06
Can you do a
```

sudo apt-get update

```
without any errors?

---

### Post by badboyz107 on 2008-03-06
yes I can...seems to be the only thing lol

---

### Post by badboyz107 on 2008-03-07
Oh please help a poor beggin man out!!:confused:

---

### Post by jan quark on 2008-03-07
try these commands and see what happens ...
post the errors which pop up
```

sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by badboyz107 on 2008-03-07
#@troy-desktop:~$ sudo dpkg --configure -a
Password:
#@troy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

Okay so what did that do??  Nothing?  LOL

---

### Post by kesman on 2008-03-07
```

sudo apt-get dist-upgrade

```

Does this give any errors?

---

### Post by badboyz107 on 2008-03-07
oddly enough....yes


#@troy-desktop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  hal-info libcurl3-gnutls libmtp5
The following packages will be upgraded:
  evolution evolution-common evolution-plugins gnome-btdownload gnupg gpgv hal
  hal-device-manager lftp libhal-storage1 libhal1 rhythmbox tzdata
13 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.3MB of archives.
After unpacking 1761kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `linux-headers-2.6.20-16': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kesman on 2008-03-07
> Need to get 0B/31.3MB of archives.
Seems like you already have the packages, but they aren't installed. Try
```

sudo apt-get clean

```
to remove downloaded packages and then again
```

sudo apt-get dist-upgrade

```
This time it should download again the files and attempt to update.

EDIT: You could also try to reinstall tzdata, which seems to cause problems. To do this, type
```

sudo apt-get install --reinstall tzdata

```

---

### Post by badboyz107 on 2008-03-08
Grrrrrr!


#@troy-desktop:~$ sudo apt-get clean
Password:
#@troy-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  hal-info libcurl3-gnutls libmtp5
The following packages will be upgraded:
  evolution evolution-common evolution-plugins gnome-btdownload gnupg gpgv hal
  hal-device-manager lftp libhal-storage1 libhal1 rhythmbox tzdata
13 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.3MB of archives.
After unpacking 1761kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main evolution 2.10.1-0ubuntu2.1 [2539kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main tzdata 2007k-0ubuntu0.7.04.1 [316kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main libcurl3-gnutls 7.15.5-1ubuntu2.1 [164kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main gpgv 1.4.6-2ubuntu3~feisty1 [146kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main gnupg 1.4.6-2ubuntu3~feisty1 [1792kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main evolution-common 2.10.1-0ubuntu2.1 [19.4MB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main libhal1 0.5.9-1ubuntu2~feisty1 [362kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main gnome-btdownload 0.0.28-1~feisty1 [35.8kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main libhal-storage1 0.5.9-1ubuntu2~feisty1 [360kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main hal 0.5.9-1ubuntu2~feisty1 [658kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main hal-info 20070402-1ubuntu1~feisty1 [29.8kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main hal-device-manager 0.5.9-1ubuntu2~feisty1 [403kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main lftp 3.5.11-1~feisty1 [535kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libmtp5 0.1.3-0ubuntu2 [92.7kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main rhythmbox 0.11.2-0ubuntu4~feisty1 [4416kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main evolution-plugins 2.10.1-0ubuntu2.1 [130kB]
Fetched 31.3MB in 5m32s (94.3kB/s)                                             
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `linux-headers-2.6.20-16': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by badboyz107 on 2008-03-08
DOUBLE GRRRR



#@troy-desktop:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/316kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `linux-headers-2.6.20-16': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2007k-0ubuntu0.7.04.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by itsjustarumour on 2008-03-08
I'm getting something very similar since the Gutsy updates 2 days ago. The above suggestions don't fix it for me either.  Trying to update or install anything, I get:

> E: tzdata: subprocess post-installation script returned error exit status 1

Trying

> sudo dpkg-reconfigure -a

gives me

> ian@COOLERMASTER:~$ sudo dpkg-reconfigure -a
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
ian@COOLERMASTER:~$ 


Trying 

> sudo apt-get install --reinstall tzdata

gives me

> ian@COOLERMASTER:~$ sudo apt-get install --reinstall tzdata
[sudo] password for ian:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Setting up tzdata (2007k-0ubuntu0.7.10.1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


***EDIT*** - just as an update, I've tried using Synaptic to force-downgrade to the previous version of tzdata, but no joy.

Help!!

---

### Post by itsjustarumour on 2008-03-08
I've just tried 

> dpkg -s tzdata

which gives me

> ian@COOLERMASTER:~$ dpkg -s tzdata
Package: tzdata
Status: install ok half-configured
Priority: required
Section: libs
Installed-Size: 6136
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Architecture: all
Version: 2007k-0ubuntu0.7.10.1
Config-Version: 2007k-0ubuntu0.7.10
Replaces: libc0.1, libc0.3, libc6, libc6.1, locales
Depends: debconf | debconf-2.0
Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
ian@COOLERMASTER:~$ 



Does anybody know how I should complete the configuration of tzdata?  

> sudo dpkg-reconfigure tzdata

just gives me:

> ian@COOLERMASTER:~$ sudo dpkg-reconfigure tzdata
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
ian@COOLERMASTER:~$ 


:-(

---

### Post by itsjustarumour on 2008-03-08
Bump.

---

### Post by deadlikeoscar on 2008-03-09
I'm getting the same error when I try to update in Feisty. That is actually why I am still using Feisty. I have had this problem for months and have been unable to find an answer. I fsck'd my drive and it found errors but afterwards the problem remained. I am interested to see the outcome of this thread.

---

### Post by itsjustarumour on 2008-03-09
Bump!

---

### Post by itsjustarumour on 2008-03-09
OK, well I don't know if this will help anybody having problems with tzdata, but I've managed to fix my problem with the "E: tzdata: subprocess post-installation script returned error exit status 1" error message.

The key clue (for me at least) was that 

> sudo dpkg-reconfigure tzdata

gave me:

> ian@COOLERMASTER:~$ sudo dpkg-reconfigure tzdata
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
[email]ian@COOLERMASTER:~$/var/cache/debconf/config.dat[/email]

On checking, this config.dat file didn't exist, so I just recreated it:

> sudo nautilus

Create a new folder in /var/cache/ called "debconf" (without the quotes)

> sudo gedit

Save this blank text file as "config.dat" (without the quotes) into your newly-created /var/cache/debconf/ folder, and Bob's yer Uncle!

:-)

---

### Post by badboyz107 on 2008-03-11
So this thang crashed hard the other day so I thought "hey self lets do a clean install and see what happens"  No Joy!!


> #@troy-desktop:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
31 not fully installed or removed.
Need to get 0B/316kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 106098 files and directories currently installed.)
Preparing to replace tzdata 2007k-0ubuntu0.7.04.1 (using .../tzdata_2007k-0ubuntu0.7.04.1_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2007k-0ubuntu0.7.04.1) ...
Current default timezone: 'America/North_Dakota/New_Salem'.
Local time is now:      Tue Mar 11 07:39:35 CDT 2008.
Universal Time is now:  Tue Mar 11 12:39:35 UTC 2008.
Run 'tzconfig' if you wish to change it.

Setting up cupsys (1.2.8-0ubuntu8.2) ...
 * Starting Common Unix Printing System: cupsd                                  /etc/init.d/cupsys: 95: touch: Input/output error
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-common (2.2.0-1ubuntu5) ...
Updating OpenOffice.org's dictionary list... done.
/var/lib/dpkg/info/openoffice.org-common.postinst: 85: touch: Input/output error
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 2
Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ] 
/var/lib/dpkg/info/apport.postinst: 19: touch: Input/output error
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/var/lib/dpkg/info/capplets-data.postinst: 19: touch: Input/output error
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up evolution-common (2.10.1-0ubuntu2.1) ...
/var/lib/dpkg/info/evolution-common.postinst: 14: touch: Input/output error
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.10.1-0ubuntu2.1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.10.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (2.0.0.12+1nobinonly+2-0ubuntu0.7.4) ...
/var/lib/dpkg/info/firefox.postinst: 13: touch: Input/output error
dpkg: error processing firefox (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 2.0.0.12+1nobinonly+2-0ubuntu0.7.4); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-app-install (0.3.31) ...
/var/lib/dpkg/info/gnome-app-install.postinst: 7: touch: Input/output error
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/var/lib/dpkg/info/gnome-panel-data.postinst: 34: touch: Input/output error
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.6-16.30) ...
/sbin/lrm-manager: 41: touch: Input/output error
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--07:40:53--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--07:40:53--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--07:40:54--  [http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--07:40:54--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--07:40:54--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
           => `./andale32.exe?download&failedmirror=switch.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--07:40:54--  [http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
           => `./andale32.exe?download&failedmirror=switch.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--07:40:55--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384       80.74K/s             

07:40:57 (80.58 KB/s) - `./andale32.exe' saved [198384/198384]

/usr/sbin/update-ms-fonts: 181: touch: Input/output error
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.24-2ubuntu1.5) ...
Bus error (core dumped)
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.24-2ubuntu1.5); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/var/lib/dpkg/info/sun-java6-bin.postinst: 80: touch: Input/output error
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not configured yet.
 sun-java6-plugin depends on firefox | iceweasel | mozilla-firefox | iceape | mozilla-browser | epiphany-browser | galeon | konqueror; however:
  Package firefox is not configured yet.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-browser is not installed.
  Package galeon is not installed.
  Package konqueror is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up tomboy (0.6.3-0ubuntu1.1) ...
/var/lib/dpkg/info/tomboy.postinst: 34: touch: Input/output error
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
 ubuntu-restricted-extras depends on sun-java6-plugin; however:
  Package sun-java6-plugin is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-system-tools (2.18.1-0ubuntu2) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: 24: touch: Input/output error
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cupsys
 hplip
 openoffice.org-common
 apport
 apport-gtk
 capplets-data
 evolution-common
 evolution
 evolution-plugins
 firefox
 firefox-gnome-support
 gnome-app-install
 gnome-control-center
 gnome-panel-data
 gnome-panel
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
 msttcorefonts
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org-filter-mobiledev
 openoffice.org
 openoffice.org-evolution
 samba-common
 smbclient
 sun-java6-bin
 sun-java6-plugin
 tomboy
 ubuntu-restricted-extras
 gnome-system-tools
sh: touch: Input/output error
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by badboyz107 on 2008-03-11
I downloaded Gutsy but cant burn it to a CD because it tells me to insert a blank cd....well it IS!

---

### Post by badboyz107 on 2008-03-11
Damn!  I cant even upgrade to Gutsy without the computer crashing and having to do a clean install of Feisty...

What in the hell is going on here??

---

