---
title: "Can't install Opera from Canonical repository"
date: 2007-05-21
forum: General Help
---

### Post by greenstar on 2007-05-21
I can't get Opera to install from the repos, and I added the Canonical Commercial repo the day of installation (over a month ago). I still cannot install Opera from repos. Here's what I do:

```
sudo aptitude install opera
``````
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for opera
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

So, then I check my sources.list:

```
sudo gedit /etc/apt/sources.list
```

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Add comments (##) in front of any line to remove it from being checked.   
# Use the following sources.list at your own risk.  

# Uncomment deb-src if you wish to download the source packages

# If you have a install CD you can add it to the reposity using 'apt-cdrom add'
# which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted

## Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

## Ubuntu community supported packages
# Software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# team, and may not be under a free licence. Please satisfy yourself as to
# your rights to use the software. Also, please note that software in
# multiverse WILL NOT receive any review or updates from the Ubuntu
# security team.
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

## Ubuntu backports project
# Uncomment the following two lines to add software from the 'backports'
# repository.
# Software from this repository may not have been tested as
# extensively as that contained in the main release, although it includes
# newer versions of some applications which may provide useful features.
# Also, please note that software in backports WILL NOT receive any review
# or updates from the Ubuntu security team.
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

## Medibuntu - Ubuntu 7.04 "feisty fawn"
# For GPG errors, use this line at the terminal: 
# wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
# PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## Commercial software
# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
# servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Sub-pixel font rendering
# This will dramatically improve the appearance of fonts with respect to
# the default Ubuntu install.
#If you get errors about missing gpg key, do the following 2 lines
# in a terminal, leaving off the '#' at the beginning.
# gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
# gpg --export --armor 937215FF | sudo apt-key add -
deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
# For GPG errors, use this line at the terminal: 
# wget -q http://lut1n.ifrance.com/repo_key.asc -O- | sudo apt-key add -
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

## Super Nintendo Emulator (ZSNES) 1.510 for i386/AMD64
deb http://packages.dfreer.org feisty main

## Current Wine (needed for IEs4Linux)
deb http://wine.budgetdedicated.com/apt feisty main

## Avant Window Navigator (needs XGL/AIGLX + Beryl/Compiz)
# Enter the following to get GPG key:
# wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

```

I must be overlooking something simple. Anyone have any idea what's wrong?

Greenstar

---

### Post by newlinux on 2007-05-21
did you do:

sudo aptitude update

after adding the repo but before the install command?

---

### Post by Swab on 2007-05-21
You actually need the following repo with Feisty...

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

---

### Post by zvacet on 2007-05-21
Download it from here

[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by greenstar on 2007-05-21
> **newlinux said:**
> did you do:

sudo aptitude update

after adding the repo but before the install command?

Yes, I've had the repo on my list for some time and I have updated numerous times since.

Everyone: thanks for the quick responses, you are appreciated.

Greenstar

---

