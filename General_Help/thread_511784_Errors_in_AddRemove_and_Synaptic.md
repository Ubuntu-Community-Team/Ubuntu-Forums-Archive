---
title: "Errors in Add/Remove and Synaptic"
date: 2007-07-28
forum: General Help
---

### Post by Rosemere on 2007-07-28
*I am trying to resolve how to get my Add/Remove  application working or synapatic program manager.*

I can only access Synaptic preferences by Right Clicking the icon on the toolbar and that only gets me to software sources.
Below are messages I have received. I also  tried to see if I am missing anything in Debian as I noticed 
I cannot access from Applications.

If you think you know what steps I can do to repair my problems could you be so nice to   write the basic steps I should take when opening Terminal. Not have me go back to web sites.

I believe most of this problem happened after I tried to install flash player. I also cannot access the respositories.

When I was trying to install Automatix  and Wine I might have messed the system up. Everyone has told me to just change   the deb-sr TO deb-src  but how does one do that from the Terminal.
I tried to post in the Beginner forum with no success, I am just a Newborn.

“deb-sr

c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties”

Failed to check for installed and available applications



This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Could not download all repository indexes


The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

E: Type 'deb-sr' is not known on line 5 in source list /etc/apt/sources.list

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.



sudo apt-get install Debian

apt-cache search Debian

pete@pete-desktop:~$ apt-cache search Debian

libavcodec0d - ffmpeg codec library - Medibuntu package

libavformat0d - ffmpeg file format library - Medibuntu package

libpostproc0d - ffmpeg video postprocessing library - Medibuntu package

googleearth - Google Earth! - Explore, Search and Discover - binary files

java-common - Base of all Java packages

debconf - Debian configuration management system

dash - The Debian Almquist Shell

debianutils - Miscellaneous utilities specific to Debian

openoffice.org - OpenOffice.org Office suite

libsdl1.2debian - Simple DirectMedia Layer

linux-headers-2.6.20-15-generic - Linux kernel headers for version 2.6.20 on x86/x86_64

python-minimal - A minimal subset of the Python language (default version)

autotools-dev - Update infrastructure for config.{guess,sub} files

ucf - Update Configuration File: preserves user changes to config files.

bsdutils - Basic utilities from 4.4BSD-Lite

gjdoc - documentation generation framework for java source files

lsb-release - Linux Standard Base version reporting utility

debhelper - helper programs for debian/rules

dpkg-dev - package building tools for Debian

vim-common - Vi IMproved - Common files

python2.5-minimal - A minimal subset of the Python language (version 2.5)

apt - Advanced front-end for dpkg

sgml-base - SGML infrastructure and SGML catalog file support

python - An interactive high-level object-oriented language (default version)

doc-base - utilities to manage online documentation

xserver-xorg-input-evdev - X.Org X server -- evdev input driver

tar - GNU tar

adduser - Add and remove users and groups

tasksel - Tool for selecting tasks for installation on Debian systems

python-dev - Header files and a static library for Python (default)

cli-common - common files between all CLI (.NET) packages

base-files - Debian base system miscellaneous files

pcmciautils - PCMCIA utilities for Linux 2.6

tasksel-data - Official tasks used for installation of Debian systems

linux-headers-2.6.20-16 - Header files related to Linux kernel version 2.6.20

linux-headers-2.6.20-15 - Header files related to Linux kernel version 2.6.20

apmd - Utilities for Advanced Power Management (APM)

odbcinst1debian1 - Support library and helper program for accessing odbc ini files

intltool-debian - Help i18n of RFC822 compliant config files

gs-common - Common files for different Ghostscript releases

xfonts-scalable - scalable fonts for X

base-passwd - Debian base system master password and group files

linux-headers-2.6.20-16-generic - Linux kernel headers for version 2.6.20 on x86/x86_64

x11-common - X Window System (X.Org) infrastructure

python-problem-report - python library to handle problem reports

foomatic-filters - OpenPrinting printer support - filters

libsdl1.2debian-alsa - Simple DirectMedia Layer (with X11 and ALSA options)

sgml-data - common SGML and XML data

passwd - change and administer password and group data

libpam-runtime - Runtime support for the PAM library

foomatic-db-engine - OpenPrinting printer support - programs

initscripts - Scripts for initializing and shutting down the system

gstreamer0.10-pitfdll - GStreamer plugin for using MS Windows binary codecs

e2fsprogs - ext2 file system utilities and libraries

gzip - The GNU compression utility

dpkg - package maintenance system for Debian

aptitude - terminal-based apt frontend

build-essential - informational list of build-essential packages

anacron - cron-like program that doesn't go by time

info - Standalone GNU Info documentation browser

debaux - Debian Auxiliary Programs

dselect - user tool to manage Debian packages

alsa-base - ALSA driver configuration files

xml-core - XML infrastructure and XML catalog file support

nano - free Pico clone with some new features

python-apt - Python interface to libapt-pkg

foomatic-db - OpenPrinting printer support - database

defoma - Debian Font Manager -- automatic font configuration framework

automatix2 - Automatix is a graphical interface for automating the installation of the most commonly requested applications in Debian based linux operating systems.

iptables - administration tools for packet filtering and NAT

make - The GNU version of the "make" utility.

ttf-indic-fonts - Metapackage for free Indian language fonts

scim - smart common input method platform

ca-certificates - Common CA Certificates PEM files

python2.4-minimal - A minimal subset of the Python language (version 2.4)

pete@pete-desktop:~$ 

pete@pete-desktop:~$

---

### Post by forestpixie on 2007-07-28
in terminal do

```
gedit /etc/apt/sources.list
```

and post the text here

as far as Debian in the menu goes - you have to do a couple of steps to get the Debian stuff to show - but can't remember what at the moment

---

### Post by Rosemere on 2007-07-28
[COLOR="Blue"]Below you will see my source list. You will see line five has an error BUT HOW do I make the change and where.[/COLOR]

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty universe restricted main
deb-sr
deb-
scr [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

## Major  bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-proposed universe restricted main
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-proposed universe restricted #Added by software-properties
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports universe restricted main
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports universe restricted #Added by software-properties

#AUTOMATIX REPOS START

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports multiverse #Added by software-properties



deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty multiverse #Added by software-properties

---

### Post by forestpixie on 2007-07-28
```
> **Rosemere said:**
> [COLOR="Blue"]Below you will see my source list. You will see line five has an error BUT HOW do I make the change and where.[/COLOR]

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty universe restricted main
[COLOR="Red"]deb-sr[/COLOR]
[COLOR="Red"][COLOR="YellowGreen"]deb-
scr[/COLOR][/COLOR] [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

## Major  bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-proposed universe restricted main
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-proposed universe restricted #Added by software-properties
deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports universe restricted main
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports universe restricted #Added by software-properties

#AUTOMATIX REPOS START

deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty-backports multiverse #Added by software-properties



deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty multiverse
deb-src [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty multiverse #Added by software-properties
```

ok first we need to make a backup

in a terminal do this

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.2807
```

once you've done that in terminal

```
gksudo gedit /etc/apt/sources.list
```

you will get a text editor with your sources list in it 

I have higlighted the part of your sources list in red at line 5 above in the quote - put the cursor there and delete until it has all gone.

Then the bit in green which shows as

```
deb-
scr
```

needs to read as 
```

deb-src 
```

once that line has been edited that part of your sources list should look like this

```
deb http://mirrors.easynews.com/linux/ubuntu/ feisty universe restricted main
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties
```

save and exit

then in terminal 

```
sudo apt-get update
```

If thta doesn't make sense to you - ask

---

### Post by Rosemere on 2007-07-28
After  saved and exit  this is the message I get in Terminal.  Also went back amd retrieved a new source list.  Somewhere I entered something incorrect as I copied your directions into Office.

pete@pete-desktop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.2807

Password:

pete@pete-desktop:~$ gksudo gedit /etc/apt/sources.list

pete@pete-desktop:~$ sudo apt-get update

E: Type 'deb-scr' is not known on line 6 in source list /etc/apt/sources.list

pete@pete-desktop:~$ 




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty universe restricted main



deb-scr [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties



## Major  bug fix updates produced after the final release of the

## distribution.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.gksu gedit /etc/apt/sources.list

---

### Post by forestpixie on 2007-07-28
my instructions say  change 

deb-
scr

to deb-src 

that's the problem with line 6

do the 

gksudo gedit /etc/apt/sources.list

and change that

save

and redo

sudo apt-get update

again

---

### Post by Rosemere on 2007-07-28
Sorry still messing up. Here are two pics to show what I did.[IMG]http://img.photobucket.com/albums/v281/harbourwoods/Pic1.jpg[/IMG]
and 
[IMG]http://img.photobucket.com/albums/v281/harbourwoods/Pic2a.jpg[/IMG]

Now here is the lastest from my source list. I think I should go back to school to learn how to follow directions. Please don't give up on me. Maybe the screen shots will help.


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb-scr [http://mirrors.easynews.com/linux/ubuntu/](http://mirrors.easynews.com/linux/ubuntu/) feisty universe restricted main

deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

## Major  bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list

---

### Post by forestpixie on 2007-07-28
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb-[COLOR="Red"]scr[/COLOR] http://mirrors.easynews.com/linux/ubuntu/ feisty universe restricted main

deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.gksu gedit /etc/apt/sources.list
__________________
```


quite simply there should be NO occurences of

deb-scr

they should be 

deb-src

you need to do the gksudo gedit /etc/apt/sources.list 

and change all the scr's to src

I'm not going to give up - yet:D, don't go adding thing else to the file just yet

when you've edited the file 

do 
sudo apt-get update

if you get a problem - please post the sources.list file again so I can look again :)

---

### Post by Rosemere on 2007-07-28
:)
Thank you, Thank you we have Add/Remove and synaptic back.
I realize now I reversed letters. :x
I wish I could buy you a glass of wine for being so patient.
I am back to where I started a week ago re Repositores and Software sources. 

Tell me when you will be on line again so I can post those issues. Obviously the screen shot made the difference

---

### Post by forestpixie on 2007-07-28
Well done - I've seen your other threads on the same problem - keep going I'd say :)

have a look at these 2 pages, the second one will help you get repos. 

Assuming you're using Ubuntu - go to system>admin>software sources and make sure the main, universe, multiverse  aand restricted are ticked.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Before you do anything to any files make sure you have backed it up

sudo cp /location/filename /location/filename.bak

then you can get back easily enough - check out the man pages for cp, mv.

Now if you're needing to add repos - which ones are you trying to add?

---

