---
title: "made a mistake"
date: 2006-12-29
forum: General Help
---

### Post by gatorbowls on 2006-12-29
I was editing this file sudo gedit /etc/apt/sources.list  but i messed up and sorta somewhat saved it :(..and i dident make a backup of it...can someone please post  there copy of this file  thanks

---

### Post by raul_ on 2006-12-29
just open it again and undo it :mrgreen: try this link [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by darco on 2006-12-29
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by d3v1ant_0n3 on 2006-12-29
Be aware that dapper and edgy sources.list files are different!

---

### Post by LosingMyPigeon on 2006-12-29
open a terminal

cd /etc/apt/

sudo touch sources.list  //Create file

Go back and launch Synaptic Package Manager -->  Settings --> Repositories.

Then on tab 1, check all the boxes.  Then on tab 2, check all the boxes.  Click "Close" (OK).

This should get you back up and running with basics in a pinch.

After this, go to cd /etc/apt and create a backup in case you lose your ability to use Gnome Desktop and can't skate by with Synaptic.

Finally, file a suggestion for the next Ubunto to ship with a sources.list.default file or sources.list.orig auto-magically in the /etc/apt folder.  Also, Synaptic should have a "Reset to Defaults" option on the Synaptic Package Manager -->  Settings --> Repositories -->Tab "Ubuntu X.XX in the next release.

Be careful about pasting in other peoples entire files.  Good luck.

---

### Post by LosingMyPigeon on 2006-12-29
Better yet:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Ignore my hack above.

---

