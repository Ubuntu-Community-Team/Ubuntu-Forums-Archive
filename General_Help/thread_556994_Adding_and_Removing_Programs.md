---
title: "Adding and Removing Programs"
date: 2007-09-22
forum: General Help
---

### Post by shoaibnawaz on 2007-09-22
I have used snaptic to Add/Remove programs. I have downloaded many packages from it. But last time I did something in Preferences of it. Now it is showing a dialogue box conveying a message about Major error in Software Management System.
According to it.
How to check the broken packages?
How to check the file permission and correctness of sources.list file?

I am pasting the file contents of sources.list here
========================================
LINE 1:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
LINE 2:# newer versions of the distribution.
LINE 3:
LINE 4:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty main restricted
LINE 5:
LINE 6:## Major bug fix updates produced after the final release of the
LINE 7:## distribution.
LINE 8:
LINE 9:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
LINE 10:## team, and may not be under a free licence. Please satisfy yourself as to
LINE 11:## your rights to use the software. Also, please note that software in
LINE 12:## universe WILL NOT receive any review or updates from the Ubuntu security
LINE 13:## team.
LINE 14:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty universe
LINE 15:
LINE 16:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
LINE 17:## team, and may not be under a free licence. Please satisfy yourself as to 
LINE 18:## your rights to use the software. Also, please note that software in 
LINE 19:## multiverse WILL NOT receive any review or updates from the Ubuntu
LINE 20:## security team.
LINE 21:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty multiverse
LINE 22:
LINE 23:## Uncomment the following two lines to add software from the 'backports'
LINE 24:## repository.
LINE 25:## N.B. software from this repository may not have been tested as
LINE 26:## extensively as that contained in the main release, although it includes
LINE 27:## newer versions of some applications which may provide useful features.
LINE 28:## Also, please note that software in backports WILL NOT receive any review
LINE 29:## or updates from the Ubuntu security team.
LINE 30:# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
LINE 31:# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
LINE 32:
LINE 33:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
LINE 34:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
LINE 35:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
LINE 36:deb [http://archive.ubuntu.com/ubuntu/dists](http://archive.ubuntu.com/ubuntu/dists) feisty
LINE 37:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
========================================
On some places it shows problem on line 36.
How can I resolve it Please guide me in this regard.

---

### Post by klytu on 2007-09-22
> **shoaibnawaz said:**
> I have used snaptic to Add/Remove programs. I have downloaded many packages from it. But last time I did something in Preferences of it. Now it is showing a dialogue box conveying a message about Major error in Software Management System.
According to it.
How to check the broken packages?
How to check the file permission and correctness of sources.list file?

I am pasting the file contents of sources.list here
========================================
LINE 1:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
LINE 2:# newer versions of the distribution.
LINE 3:
LINE 4:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty main restricted
LINE 5:
LINE 6:## Major bug fix updates produced after the final release of the
LINE 7:## distribution.
LINE 8:
LINE 9:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
LINE 10:## team, and may not be under a free licence. Please satisfy yourself as to
LINE 11:## your rights to use the software. Also, please note that software in
LINE 12:## universe WILL NOT receive any review or updates from the Ubuntu security
LINE 13:## team.
LINE 14:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty universe
LINE 15:
LINE 16:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
LINE 17:## team, and may not be under a free licence. Please satisfy yourself as to 
LINE 18:## your rights to use the software. Also, please note that software in 
LINE 19:## multiverse WILL NOT receive any review or updates from the Ubuntu
LINE 20:## security team.
LINE 21:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty multiverse
LINE 22:
LINE 23:## Uncomment the following two lines to add software from the 'backports'
LINE 24:## repository.
LINE 25:## N.B. software from this repository may not have been tested as
LINE 26:## extensively as that contained in the main release, although it includes
LINE 27:## newer versions of some applications which may provide useful features.
LINE 28:## Also, please note that software in backports WILL NOT receive any review
LINE 29:## or updates from the Ubuntu security team.
LINE 30:# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
LINE 31:# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
LINE 32:
LINE 33:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
LINE 34:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
LINE 35:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
LINE 36:deb [http://archive.ubuntu.com/ubuntu/dists](http://archive.ubuntu.com/ubuntu/dists) feisty
LINE 37:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
========================================
On some places it shows problem on line 36.
How can I resolve it Please guide me in this regard.
Try putting a "#" in front of line 36 (this comments it out so it is ignored). Also, I think your line 37 should probably be > deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe  Did you make a lot of changes to your sources.list without backing it up first?

---

