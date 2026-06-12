---
title: "APTonCD and synaptic trouble"
date: 2007-12-10
forum: General Help
---

### Post by RockTonic3 on 2007-12-10
Ever since I made a backup cd with APTonCD, if i try to install a program from terminal, add/remove, or synaptic package manager, it asks me to put the cd in.  I don't know where i put the cd so i can't do that and if i push cancel it won't get the application from the repositories.  how do i make it stop doing this?

---

### Post by theZest on 2007-12-10
Just erase or comment Aptoncd string in sources.list

---

### Post by logos34 on 2007-12-10
like this:

gksudo gedit /etc/apt/sources.list

> # deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
# deb cdrom:[APTonCD for ubuntu gutsy - amd64 (2007-11-26 15:38) CD1]/ /
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

---

### Post by RockTonic3 on 2007-12-10
yeah...  you know, i'm not sure why i didn't think to just look there :)  it's weird, apparently APTonCD disables all of the internet repositories?  I wasn't even getting updates.  

thanks for the help

---

