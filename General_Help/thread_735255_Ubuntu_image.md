---
title: "Ubuntu image?"
date: 2008-03-25
forum: General Help
---

### Post by jhyland87 on 2008-03-25
Hey guys, so I wanted to make an image of ubuntu desktop with beryl and wine installed, I have made an image with windows before using nero... I was told its way different than making an image on linux..

What program do I use? And anyone here have a tutorial in mind?

---

### Post by scragar on 2008-03-25
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
or
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

both work well and have full guides and easy menu's.

---

### Post by jhyland87 on 2008-03-25
> **scragar said:**
> [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
or
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

both work well and have full guides and easy menu's.

wow, reconstructioner lets you make the image and have it so you can run it in live mode????

---

### Post by scragar on 2008-03-25
both do

---

### Post by evilc on 2008-03-25
Have a look at the program called Remastersys, it can make a distro/backup of your installation. Maybe better way.

---

### Post by jhyland87 on 2008-03-27
Has anyone made a tutorial for reconstructor, I cant find one... Im new to linux, and I cant install the distro because I cant find the distro link, the DL hyperlink is a diff page that lets you download it.

---

### Post by scragar on 2008-03-27
it's not a distro, it's just an easy method of backup up your full install

[http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=5](http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=5) <-- download and install the latest stable(you want the debian package).

install by double clicking the .deb, or using the command line. Once installed go:
Applications > System Tools > reconstructor
then follow instructions.

---

### Post by jhyland87 on 2008-03-27
I tried that, it said the software index is broken

---

### Post by jhyland87 on 2008-03-27
[IMG]http://i66.photobucket.com/albums/h247/farfromeinstein/wtf.png[/IMG]

ughhhhhhhh

---

### Post by scragar on 2008-03-27
just follow the instructions(and please link to the image instead of posting it):

firstly, find out what's wrong or comment out line 56 of the sources list:
```
sudo gedit /etc/apt/sources.list
```

then run update and fix any broken packages:
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by jhyland87 on 2008-03-27
deb ~/home/administrator/Desktop/reconstructor_2.7_all.deb Gutsy main

do I gave something in the wrong folder?

---

### Post by scragar on 2008-03-27
just remove that line all together, you've downloaded the package so there is no need to link to it in your lists(esspecialy since it's not a repository)

---

### Post by jhyland87 on 2008-03-27
oh wow, thats easier than I would have thought.

Ok I waiting for it co copy the files off the iso file I downloaded from ubuntu

---

### Post by jhyland87 on 2008-03-27
interesting, I selected live cd and left the field blank so I could use the live cd, does that just burn the live cd and not any of the settings I have saved on my current computer?

---

### Post by jhyland87 on 2008-03-27
ok it made an image, but not with any of the programs I have on here. I wanted it to maket he image with wine and CCSM

---

### Post by Wobblybob on 2008-04-09
To add wine to the Reconstructor app you need to add a module in /usr/share/reconstructor/modules, they are text docs so you can open them in a text editor and amend them. the one I use to load wine is as follows;

*********************************************************************

#!/bin/sh
#
# Reconstructor Module - Wine - Windows Emulator
#	Copyright (c) 2006  Reconstructor Team <http://reconstructor.aperantis.com>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

RMOD_ENGINE=1.0
RMOD_CATEGORY='Software'
RMOD_SUBCATEGORY='Virtualization'
RMOD_NAME='Install Wine'
RMOD_AUTHOR='WobblyBob'
RMOD_VERSION=0.1
RMOD_DESCRIPTION='Wine - Windows Emulator'
RMOD_RUN_IN_CHROOT=True
RMOD_UPDATE_URL='http://reconstructor.aperantis.com/update/modules/'
echo Running $RMOD_NAME...

#install wget
sudo apt-get install -y wget

#add the repository's key to your system's list of trusted APT keys
sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

#add the repository for Ubuntu Gutsy (7.10)
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

#upate the source list
sudo apt-get update

#install Wine
sudo apt-get install wine

# clean up
apt-get clean
apt-get autoclean

echo $RMOD_NAME Finished...

*************************************************************************

When to add a module it will show up in the [customization], [modules] section of reconstructor. If you check out the Download/modules section of the Reconstructor site there are other pre made modules available to add and remove apps.

There is a user guide in pdf format [here]("http://files.filefront.com/Reconstructor+guidepdf/;8845802;/fileinfo.html/") which helped me.

---

