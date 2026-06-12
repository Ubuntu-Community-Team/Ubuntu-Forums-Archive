---
title: "The Expanded Hardy sources.list thread?"
date: 2008-05-02
forum: General Help
---

### Post by Glaxed on 2008-05-02
I've been trying to track down several repositories and write a shell script to take the pain away from expanding your sources.list.

However, finding good repositories and getting them to work without errors is mind-numbing...

This is what I have so far, *I would really appreciate it if people could help me expand and correct this list.*

[LEFT]This isn't just a collection of bleeding software that breaks your system most of the time, it just has useful or important software not in the original list - and I hope it stays that way.
[/LEFT]
Many users feel awkward about packages that non-MOTUs and non-devs make, but I have never run into a single problem while using them in Feisty (trevino's list), Gutsy (skymera+1337455 10534), or Hardy (oshelpdesk). Still, **use this at your own risk.**
For the record; with this current list - **I have had flawless compiz, gtk, codecs, apparmor, and kernel upgrades.**

**_The installer (setup.sh) -_**
- Instructions: Download the attatched hardylist.tar.bz2, extract it onto your desktop, and open a terminal. Type 
```

cd ~/Desktop/hardylist
sudo chmod a+x setup.sh
./setup.sh

```and follow the instructions there.
setup.sh code;
```

#!/bin/bash
# Note;
# I am mainly a Python and C++ programmer - I know nothing of writing shell scripts,
# so forgive me. I've tried to make the code here readable...

echo "# Experimental Expanded Hardy Sources List"
echo "# - Brought to you by vminch000/Glaxed"
echo
echo "This script will;"
echo "  * back up your old sources.list"
echo "  * replace it with a continually updated new sources.list"
echo "  * and resolve issues with the new list"
echo "          - (GPG, Igns, Errs - nothing serious)"
echo
echo ">>> Why bother replacing the current sources.list?"
echo "This new one includes more repositories, hence more upgrades."
echo "New software in these repositories may not integrate well with"
echo "your computer, so PLEASE USE THIS AT YOUR OWN RISK."
echo "I (vminch@gmail.com) will be glad to help you with any problems"
echo "you may encounter, however I will not take responsibility for any"
echo "negative repercussions of this script/sources.list."
echo
echo ">>> If you are not sure you want to do this, please exit the terminal."
echo "To continue, hit enter."
read

echo
indir=~/Desktop
#/home/$USER/Desktop
echo "# Working in $indir."
echo

echo "OK - Working... Please be patient."
echo "# Operations:"

echo "Set up New sources.list and back up old one."
sudo mv /etc/apt/sources.list $indir/OLDsources.list
sudo mv $indir/sources.list /etc/apt/sources.list

echo "Updates"
sudo apt-get update
sudo apt-get upgrade

echo "Keys"
echo
echo "--------------------------------------------------------"

echo "# Base Check; Main, Canonical/Partner"
gpg --keyserver subkeys.pgp.net --recv-keys 437D05B5
gpg --export --armor 437D05B5 | sudo apt-key add -
gpg --keyserver subkeys.pgp.net --recv-key 6A423791
gpg --fingerprint 6A423791
gpg --armor --export  6A423791| apt-key add -

echo "# Seveas"
wget http://seveas.theplayboymansion.net/seveas/1135D466.gpg -O- | sudo apt-key add -
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

echo "# Medibuntu"
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get install medibuntu-keyring geole-keyring

echo "# Morgoth"
wget -O - http://morgoth.free.fr/files/morgoth-signkey.gpg.asc | sudo apt-key add -

echo "# NLP"
wget http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg -O- | sudo apt-key add -
gpg --keyserver subkeys.pgp.net --recv-keys 8ABD1965
gpg --export --armor 8ABD1965 | sudo apt-key add -

echo "# Google"
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
gpg --keyserver subkeys.pgp.net --recv-keys 7FAC5991
gpg --export --armor 7FAC5991 | sudo apt-key add -

echo "# wx"
wget http://apt.wxwidgets.org/key.asc | sudo apt-key add -  

echo "# Wine"
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list




echo "--------------------------------------------------------"
echo

echo "Last ditch effort key check (http://www.thinkdigit.com/forum/showthread.php?t=74632)"
for i in $(grep -o -E "http.*\.(gpg|asc|key)" /etc/apt/sources.list); do echo -n "$i "; wget $i -q -O - | sudo apt-key add -; done; keylist=""; for key in $(grep -o "[A-Fa-f0-9]\{8\}" /etc/apt/sources.list); do if [ -z "$(echo "$keylist"|grep "$key")" ]; then keylist="$keylist $key"; gpg --keyserver subkeys.pgp.net --recv $key && gpg --export --armor $key | sudo apt-key add -; fi; done;
echo

sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean

echo "All done! (Press enter to exit.)"
read
exit

```[U][B]The sources.list -
[/B][/U]```

# Experimental/Expanded sources.list for Ubuntu by vminch000/Glaxed
# Base
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

# Added by vminch000 -

# Base-like
deb http://archive.canonical.com/ubuntu hardy-commercial main

# Medibuntu (See setup.sh for details. Current listing is odd.)
deb http://packages.medibuntu.org/ hardy non-free free
deb http://packages.medibuntu.org/ hardy-staging non-free free
deb-src http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy-staging free non-free

# Morgoth (See setup.sh for details. Seems to be working fine.)
deb http://morgoth.free.fr/ubuntu hardy-backports main
deb-src http://morgoth.free.fr/ubuntu hardy-backports main

# Seveas (http://mirror3.ubuntulinux.nl/#mirrors)
# http://mirror.ubuntulinux.nl/seveas.gpg
# Alternate mirror: http://mirror.ubuntulinux.nl
deb http://mirror2.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror2.ubuntulinux.nl gutsy-seveas all

# Debug Ubuntu Packages (https://wiki.ubuntu.com/DebuggingProgramCrash)
# Listed repos may not be currently active.
deb http://ddebs.ubuntu.com hardy main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy updates main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-security main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy main universe 
deb http://ddebs.ubuntu.com hardy-updates main universe
deb http://ddebs.ubuntu.com hardy-proposed main universe
deb http://ddebs.ubuntu.com hardy-security main universe

# Ubuntu.geole.info (http://www.geole.info/index.php?id=23&l=1)
deb http://ubuntu.geole.info/ hardy universe multiverse
#deb-src http://ubuntu.geole.info/ hardy universe multiverse
deb http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse
deb-src http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse

# Google packages (http://www.google.com/linuxrepositories/apt.html)
deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/deb/ testing non-free

# NLP (GPG key: 8ABD1965)
deb http://cl.naist.jp/ eric-n/ubuntu-nlp all hardy
deb-src http://cl.naist.jp/ ~ eric-n/ubuntu-nlp all hardy

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu gutsy main

# WxWidgets / wxPython repository at apt.wxwidgets.org
# wget-q http://apt.wxwidgets.org/key.asc-O-| sudo apt-key add --
deb http://apt.wxwidgets.org/ main wx-hardy
deb-src http://apt.wxwidgets.org/ main wx-hardy
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu Hardy main restricted 

# Swiftfox browser
deb http://getswiftfox.com/builds/debian unstable non-free 

##################################################################################################
# >>> Troublemakers - will be supported (and more of them) in the future
##################################################################################################

# Audacious
deb http://ppa.launchpad.net/sebner/ubuntu Hardy Main
deb-src http://ppa.launchpad.net/sebner/ubuntu main hardy

# Jbbr Ubuntu repository, http://ubuntu.jbbr.net
# wget-q http://ubuntu.jbbr.net/jbbr_ubuntu.asc-O-| sudo apt-key add --
deb http://ubuntu.jbbr.net/packages Hardy Main
deb-src http://ubuntu.jbbr.net/packages main hardy
# # Le dépomaniak repository (GPG key: 1D59E694)
#Http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu hardy all-depomaniak
deb-src http://ubuntu.davromaniak.eu hardy all-depomaniak

# # Ryan Kavanagh's packages (GPG key: 02544D0E)
#Http://packages.ryanak.ca/02544D0E.gpg
######## I386 Architecture only!
deb http://packages.ryanak.ca ryan-hardy all
deb-src http://packages.ryanak.ca ryan-hardy all

# # Iuculano's debian packages (GPG key: AE3BE9AA)
#http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it Hardy all
deb-src http://ubuntu.iuculano.it all hardy

deb http://wicd.longren.org Hardy all

# Upstream Scribus package repository
# gpg keyserver wwwkeys.eu.pgp.net-recv-keys EEF818CF && gpg-armor-export EEF818CF | sudo apt-key add --
deb http://debian.scribus.net/debian/ Hardy Main
deb-src http://debian.scribus.net/debian/ main hardy
deb http://debian.scribus.net/debian/ hardy non-free
deb-src http://debian.scribus.net/debian/ hardy non-free

```For people who do wish to expand the list with new entries, try to keep posts in this format;
> 
[repo name]
[setup.sh code]
[sources.list entries]
e.g
> 
Google Stuff
```

echo "# Google"
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
gpg --keyserver subkeys.pgp.net --recv-keys 7FAC5991
gpg --export --armor 7FAC5991 | sudo apt-key add -

``````

# Google packages (http://www.google.com/linuxrepositories/apt.html)
deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/deb/ testing non-free

```When you guys are testing your new sources.list, if you run into any problems and wish to post the output of your update, do this;
```

q@QXD:~/Desktop$ sudo apt-get update >> /home/username/outfile
q@QXD:~/Desktop$ python cleanout.py outfile
q@QXD:~/Desktop$ gedit outfile

```Post the outfile content - so that we don't have to look at the stuff that works :). If you don't want to, that's fine too - but my eyes start to bleed after a while of looking at this stuff.. :lolflag:
Here is the code for cleanout.py, it's in the hardylist.tar.bz2 as well.
```

#!/usr/bin/env python
from sys import argv
inputFile = open("%s" % argv[1],'r')
output = inputFile.readlines()
inputFile.close()
outFile = open('output','w')
lines = []
for line in output:
    if line[0:3] == 'Get': pass
    elif line[0:3] == 'Hit': pass
    else: lines.append(line)
    print line, line[0:3]
outFile.writelines(wri)
outFile.close()

```Current list of repos that are producing error messages;
> 
W: GPG error: [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: Failed to fetch [http://wicd.longren.org/dists/Hardy/all/binary-i386/Packages.gz](http://wicd.longren.org/dists/Hardy/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.iuculano.it/dists/Hardy/all/binary-i386/Packages.gz](http://ubuntu.iuculano.it/dists/Hardy/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/Hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/Hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/Hardy/restricted/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/Hardy/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.iuculano.it/dists/all/hardy/source/Sources.gz](http://ubuntu.iuculano.it/dists/all/hardy/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://cl.naist.jp/dists/eric-n/ubuntu-nlp/all/binary-i386/Packages.gz](http://cl.naist.jp/dists/eric-n/ubuntu-nlp/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://cl.naist.jp/dists/eric-n/ubuntu-nlp/hardy/binary-i386/Packages.gz](http://cl.naist.jp/dists/eric-n/ubuntu-nlp/hardy/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy-commercial/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/sebner/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz](http://ppa.launchpad.net/sebner/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.davromaniak.eu/dists/hardy/all-depomaniak/binary-i386/Packages.gz](http://ubuntu.davromaniak.eu/dists/hardy/all-depomaniak/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://cl.naist.jp/dists/~/eric-n/ubuntu-nlp/source/Sources.gz]("http://cl.naist.jp/dists/%7E/eric-n/ubuntu-nlp/source/Sources.gz")  404 Not Found

W: Failed to fetch [http://cl.naist.jp/dists/~/all/source/Sources.gz]("http://cl.naist.jp/dists/%7E/all/source/Sources.gz")  404 Not Found

W: Failed to fetch [http://cl.naist.jp/dists/~/hardy/source/Sources.gz]("http://cl.naist.jp/dists/%7E/hardy/source/Sources.gz")  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/sebner/ubuntu/dists/main/hardy/source/Sources.gz](http://ppa.launchpad.net/sebner/ubuntu/dists/main/hardy/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://packages.ryanak.ca/dists/ryan-hardy/all/binary-i386/Packages.gz](http://packages.ryanak.ca/dists/ryan-hardy/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.davromaniak.eu/dists/hardy/all-depomaniak/source/Sources.gz](http://ubuntu.davromaniak.eu/dists/hardy/all-depomaniak/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/main/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://packages.ryanak.ca/dists/ryan-hardy/all/source/Sources.gz](http://packages.ryanak.ca/dists/ryan-hardy/all/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/main/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/restricted/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/universe/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.jbbr.net/packages/dists/Hardy/Main/binary-i386/Packages.gz](http://ubuntu.jbbr.net/packages/dists/Hardy/Main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.jbbr.net/packages/dists/main/hardy/source/Sources.gz](http://ubuntu.jbbr.net/packages/dists/main/hardy/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ddebs.ubuntu.com/dists/hardy/updates/binary-i386/Packages.gz](http://ddebs.ubuntu.com/dists/hardy/updates/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ddebs.ubuntu.com/dists/hardy-proposed/main/binary-i386/Packages.gz](http://ddebs.ubuntu.com/dists/hardy-proposed/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ddebs.ubuntu.com/dists/hardy-proposed/restricted/binary-i386/Packages.gz](http://ddebs.ubuntu.com/dists/hardy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ddebs.ubuntu.com/dists/hardy-proposed/universe/binary-i386/Packages.gz](http://ddebs.ubuntu.com/dists/hardy-proposed/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ddebs.ubuntu.com/dists/hardy-proposed/multiverse/binary-i386/Packages.gz](http://ddebs.ubuntu.com/dists/hardy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://debian.scribus.net/debian/dists/Hardy/Main/binary-i386/Packages.gz](http://debian.scribus.net/debian/dists/Hardy/Main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://debian.scribus.net/debian/dists/main/hardy/source/Sources.gz](http://debian.scribus.net/debian/dists/main/hardy/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://debian.scribus.net/debian/dists/hardy/non-free/binary-i386/Packages.gz](http://debian.scribus.net/debian/dists/hardy/non-free/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://debian.scribus.net/debian/dists/hardy/non-free/source/Sources.gz](http://debian.scribus.net/debian/dists/hardy/non-free/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://apt.wxwidgets.org/dists/main/wx-hardy/binary-i386/Packages.gz](http://apt.wxwidgets.org/dists/main/wx-hardy/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://apt.wxwidgets.org/dists/main/wx-hardy/source/Sources.gz](http://apt.wxwidgets.org/dists/main/wx-hardy/source/Sources.gz)  404 Not Found

Side note; does anyone know why Ubuntu forums does not support tar.lzma compressed files? They are smaller than all of the rest.. next best is tar.bz2...

---

### Post by Sukarn on 2008-05-03
doing a **apt-get autoclean** before a **apt-get clean** is kind of redundant as **autoclean** lists and removes .deb files for older versions of packages for which newer versions are now available, and **clean** removes every package file that has been downloaded.

Other than that, nice effort. I personally won't be using this because I have my repos set up just the way I want, with PPAs and others for all the extra softwares I need.

---

### Post by Glaxed on 2008-05-03
Thanks, I've never quite known the difference between the two :D.

Personally, I don't see anything wrong with the source.list Hardy ships with, I just think that people who maintain decent repositories may keep them up longer if more people are interested in them.

Thanks for looking at this though!

---

### Post by Sukarn on 2008-05-03
Say, are you from India or some place close to it?

I saw the link to the Digit magazine forums in your code.

---

### Post by Glaxed on 2008-05-03
Actually, that was just a lucky google hit. I got the following code from that site (and guess where they got it from? ubuntuforums archive post :D!)...
for i in $(grep -o -E "http.*\.(gpg|asc|key)" /etc/apt/sources.list); do echo -n "$i "; wget $i -q -O - | sudo apt-key add -; done; keylist=""; for key in $(grep -o "[A-Fa-f0-9]\{8\}" /etc/apt/sources.list); do if [ -z "$(echo "$keylist"|grep "$key")" ]; then keylist="$keylist $key"; gpg --keyserver subkeys.pgp.net --recv $key && gpg --export --armor $key | sudo apt-key add -; fi; done;

---

### Post by D-- on 2008-05-06
You can add my repo at [http://repository.cinnamonpirate.com/](http://repository.cinnamonpirate.com/)

It has packages for a lot of new versions of emulators that Hardy is behind on, as well as stuff packages are not maintained for:

65816asm
65816disasm
bsnes
chibitracker
dteopt
ecm
gens
goattracker
gxmame
hareng-tool
highlyadvanced
huc
id3point
mednafen
mupen64
mupen64plus
nflate
patchrom
quasi88-bios
quasi88-sdl
romjuice
snes9x-gtk
tilemolester
tsukuyomi
ucon64
uf
uips
virtualjaguar
xkas
xm7
xm7-bios

---

### Post by Grishka on 2008-05-06
> **D-- said:**
> You can add my repo at [http://repository.cinnamonpirate.com/](http://repository.cinnamonpirate.com/)

It has packages for a lot of new versions of emulators that Hardy is behind on, as well as stuff packages are not maintained for:

65816asm
65816disasm
bsnes
chibitracker
dteopt
ecm
gens
goattracker
gxmame
hareng-tool
highlyadvanced
huc
id3point
mednafen
mupen64
mupen64plus
nflate
patchrom
quasi88-bios
quasi88-sdl
romjuice
snes9x-gtk
tilemolester
tsukuyomi
ucon64
uf
uips
virtualjaguar
xkas
xm7
xm7-bios

umm, no 64-bit packages?

---

### Post by D-- on 2008-05-07
Not unless you give me a free 64-bit computer to hammer out all the compile errors in some of the oldass software that is in there. Several of those programs haven't been update in 5~7 years, it's just no one ever created anything new to replace them. Getting that stuff to compile on my system was not fun, and I would really have no way to know if a 64-bit version could even be run.

Besides, I am constantly seeing people complaining how [__stuff here__] does not work on the 64-bit kernel. A lot of people even with 64-bit machines still just run in 32-bit. As such, these packages can reach the most users.

---

### Post by Sukarn on 2008-05-07
> **D-- said:**
> Not unless you give me a free 64-bit computer to hammer out all the compile errors in some of the oldass software that is in there. Several of those programs haven't been update in 5~7 years, it's just no one ever created anything new to replace them. Getting that stuff to compile on my system was not fun, and I would really have no way to know if a 64-bit version could even be run.

Besides, I am constantly seeing people complaining how [__stuff here__] does not work on the 64-bit kernel. A lot of people even with 64-bit machines still just run in 32-bit. As such, these packages can reach the most users.

If you don't mind me asking, is there any particular reason for having your own repository and not just creating a launchpad ppa?

Edit: Don't get me wrong, I'm just curious about knowing why people don't use the ppa and make their own repository.

---

### Post by Glaxed on 2008-05-07
D--, thsnks a lot for your interest!
As soon as I get back home I'll update the thread with for your repository, it looks like some interesting packages.

---

### Post by Grishka on 2008-05-07
> **D-- said:**
> Not unless you give me a free 64-bit computer to hammer out all the compile errors in some of the oldass software that is in there. Several of those programs haven't been update in 5~7 years, it's just no one ever created anything new to replace them. Getting that stuff to compile on my system was not fun, and I would really have no way to know if a 64-bit version could even be run.

Besides, I am constantly seeing people complaining how [__stuff here__] does not work on the 64-bit kernel. A lot of people even with 64-bit machines still just run in 32-bit. As such, these packages can reach the most users.

keep it cool. I'm not complaining, 'twas just a simple question. that's your repo and you can manage it in whichever way you see fit. however, on a side note, these 32-bit packages could indeed reach many users, if not for the 403 Forbidden error when one tries to browse through [http://repository.cinnamonpirate.com/pool/pirate/](http://repository.cinnamonpirate.com/pool/pirate/) to get one. there'd be no problem if these packages could be downloaded manually, but they can't, and Synaptic won't install packages from a 32-bit repo.

---

### Post by D-- on 2008-05-08
> **Sukarn said:**
> If you don't mind me asking, is there any particular reason for having your own repository and not just creating a launchpad ppa?

Edit: Don't get me wrong, I'm just curious about knowing why people don't use the ppa and make their own repository.

I hate the launchpad interface and really just don't care to learn how to use it. Not to mention half the time I add repositories from it, then end up not working. I'm just very much not a fan of launchpad.

That said, I build all my packages manually using a couple short scripts I wrote, and then I add them into my repository using reprepro, then upload the /dists/ folder to the Web site. When byuu and I wanted to make a repository, we found there was virtually nothing written about how to do it anywhere. This was the way we came up with and it seems to work, so we'll just keep doing it :)

> **Grishka said:**
> however, on a side note, these 32-bit packages could indeed reach many users, if not for the 403 Forbidden error when one tries to browse through [http://repository.cinnamonpirate.com/pool/pirate/](http://repository.cinnamonpirate.com/pool/pirate/) to get one. there'd be no problem if these packages could be downloaded manually, but they can't, and Synaptic won't install packages from a 32-bit repo.

Sorry, your first post came off kind of bad. Didn't mean to snap. I will look into fixing the 403 error, but I am not sure whether I have the necessary access to override the server settings with my root .htaccess file. I don't really want to deal with maintaining a NotSoFancy index file in every folder for something that changes so much ...

---

### Post by Sukarn on 2008-05-08
> **D-- said:**
> I will look into fixing the 403 error, but I am not sure whether I have the necessary access to override the server settings with my root .htaccess file. I don't really want to deal with maintaining a NotSoFancy index file in every folder for something that changes so much ...

You yourself have access to those folders, so maybe you could write a script that grabs all the files and folders in the current folder, makes a list of them, removes index.html from the list and makes html links for all the files and folders that it grabbed into the index.html
Do this recursively, and run this script every time you upload some package onto the server.

I don't know how hard this will be to do for you. I'm just making a suggestion for something that seems possible to do. I used to do stuff like this with AutoHotkey back when I was using Windows, and it was quite easy to code stuff like this with that software, but learning a whole new language (even though its quite an easy language) seems like too much work for such a small thing.

---

### Post by Grishka on 2008-05-08
> Sorry, your first post came off kind of bad. Didn't mean to snap. I will look into fixing the 403 error, but I am not sure whether I have the necessary access to override the server settings with my root .htaccess file. I don't really want to deal with maintaining a NotSoFancy index file in every folder for something that changes so much ...

I didn't mean it to sound like that. perhaps I was too blunt. I apologise if you felt offended in any way. you can probably alleviate future inconveniences of this nature by simply mentioning that your packages are 32-bit only somewhere on [http://repository.cinnamonpirate.com/](http://repository.cinnamonpirate.com/) front page.

---

### Post by Glaxed on 2008-07-15
This is long overdue - but -

I've switched to Arch Linux so I won't be maintaining the script anymore... Sorry.

---

### Post by spanhead on 2008-10-06
> **Glaxed said:**
> 
# WxWidgets / wxPython repository at apt.wxwidgets.org
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) main wx-hardy
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) main wx-hardy


After a little digging found the error in the above sources.list entry, they should read:

```

deb http://apt.wxwidgets.org/ hardy-wx main
deb-src http://apt.wxwidgets.org/ hardy-wx main

```

---

