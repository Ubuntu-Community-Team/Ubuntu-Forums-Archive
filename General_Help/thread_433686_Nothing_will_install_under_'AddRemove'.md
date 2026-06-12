---
title: "Nothing will install under 'Add/Remove'"
date: 2007-05-05
forum: General Help
---

### Post by El Lance-O on 2007-05-05
Automatix ****** everything up.

I removed it, and now when I try and install almost anything, I get a message like this (installing vlc):

> Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Here's my sources.list, which from reading around could be the problem?

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

# deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

# deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
# deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

## created by seveasplf


Help?

---

### Post by meng on 2007-05-05
Are you using Breezy? As I recall, Add/Remove programs didn't work that well under Breezy, only worked okay from Dapper onwards. Try using Synaptic instead to install stuff.

---

### Post by El Lance-O on 2007-05-05
No I'm using Feisty 7.04, fresh install.

---

### Post by Sef on 2007-05-05
> Automatix ****** everything up.


Automatix changed your source list from feisty to breezy.  That's why it is not working.  You need to change all breezy to feisty.   

Go back into your source list and do this:

Search > Replace > Search For breezy > Replace with feisty.  Note: breezy and feisty are not capitalized.

---

### Post by El Lance-O on 2007-05-05
I can't save it, I don't have permission, because I'm not the owner.

I haven't touched my computer in months, so I can't remember anything.

---

### Post by Sef on 2007-05-05
> I can't save it, I don't have permission, because I'm not the owner.

I haven't touched my computer in months, so I can't remember anything.

Read this Howto: [Change your forgotten password]("http://ubuntuforums.org/showthread.php?t=133102&highlight=forgotten+password").

---

### Post by El Lance-O on 2007-05-05
What?

I know my password.

I can't modify anything in the filesystem actually, I've just noticed that.

Everything works, beryl, everything. I just can't install anything under Add/Remove.

---

### Post by El Lance-O on 2007-05-05
b

u

m

p

---

### Post by Fireblend on 2007-05-05
sudo gedit "Insert sourceslist ubication here"

---

