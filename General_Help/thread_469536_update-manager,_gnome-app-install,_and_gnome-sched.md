---
title: "update-manager, gnome-app-install, and gnome-schedule will not start"
date: 2007-06-10
forum: General Help
---

### Post by DMM8787 on 2007-06-10
Similar errors come from launching each of these programs:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk

From what I can tell, this is a problem which resulted in the upgrade from python 2.4 to 2.5.1, but thats as much as I can figure out.. and that may be entirely incorrect.

I know there are work-arounds so I don't have to use these guis, but I'd still like to know why they have broken. 

Thanks in advance!

---

### Post by waggygee on 2007-06-11
Try using automatix

---

### Post by DMM8787 on 2007-06-16
Automatix is another way to download programs, but it is not going to fix my current issues. It seems any program I have that once used python 2.4 will not work with python 2.4.

mirage, for example, used to work perfectly but I now receive this error:

Traceback (most recent call last):
  File "/usr/bin/mirage", line 26, in <module>
    import mirage
  File "/usr/lib/python2.5/site-packages/mirage.py", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk

As I said, this is the same as the other programs. gnome-schedule, gnome-sudoku, restricted-manager.

---

### Post by DMM8787 on 2007-06-16
I installed it anyways (automatix2) and I also get the same error.

david@david-desktop:~$ automatix2
  File "/usr/bin/automatix.py", line 34, in <module>
    from resin_config import *
  File "/usr/lib/automatix2/resin_config.py", line 12, in <module>
    import gtk, gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk

---

### Post by rjonesx on 2008-04-26
I am getting the exact same error in Hardy for every app that uses Python at all. This includes update-manager, the Crash Manager, etc. It is awful and NO ONE has any idea how to fix it. I have tried here, IRC, my local uber-ubuntu-geeks. no one.

---

### Post by nyscreenwriter on 2008-04-26
can you guys help me?  Every time I try to use synpatic package manager I get this error message.  Add remove programs and update manager don't work either, and as I result I cannot upgrade to Ubuntu 8.04

E: Type 'eb' is not known on line 1 in source list /etc/apt/sources.list
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Here is my apparently corrupted source list.  I'm using the regular Intel Ubuntu.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by chazaw on 2008-04-26
I've been dealing with this since early march...No luck yet...Trying to avoid reinstall so ... still hoping.

Closest I can find is 

[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/192992]("https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/192992")

Still no help though!!

---

