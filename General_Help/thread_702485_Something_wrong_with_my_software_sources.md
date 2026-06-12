---
title: "Something wrong with my software sources"
date: 2008-02-20
forum: General Help
---

### Post by kevindubrow on 2008-02-20
Hey, when I am trying to update my sources through the terminal or through the sources program, I get errors and I was wondering if anyone could help me figure out what they were:

The first error is a box that pops up labeled "Could not download all repository indexes" and has no output in the white box.

The second error is a box that is labeled "An error has occurred" and has the following in the white output box: 
E: Type '“deb' is not known on line 60 in source list /etc/apt/sources.list
E: Unable to lock the list directory

The third error is a box that is also labeled "An error has occurred" and has the following in the white output box:
E: Type '“deb' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thanks in advance for any help!

---

### Post by kellemes on 2008-02-20
Can you please post the contents of the following file?
[B]/etc/apt/sources.list
[/B]

---

### Post by kevindubrow on 2008-02-20
Sure thing! 

# 
# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

---

### Post by kellemes on 2008-02-20
From terminal..
```

cd /etc/apt
sudo cp sources.list sources.list-backup
sudo gedit sources.list

```

Remove or comment the second line with "deb cdrom:" .. you don't need it.
Remove or comment the last line with “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

Now update the package-tree..
```

sudo apt-get update

```

Now, please tell me what error-messages are left ;-)

---

### Post by kevindubrow on 2008-02-20
Awesome. You're amazing. Thanks a lot!

Oh and everything works great now! I have no clue why that deb cdrom just became an issue though.

---

### Post by kellemes on 2008-02-20
> **kevindubrow said:**
> Awesome. You're amazing. Thanks a lot!

Oh and everything works great now! I have no clue why that deb cdrom just became an issue though.


The cdrom-line was probably left from the install.
During the installation of Ubuntu packages are fetched from cdrom so this line is needed, but after install you *normally* get packages from online-repositories so your cdrom-repository isn't needed anymore..

The last line had double quotes for some reason, never heard of double quotes in sources.list so I assumed this was an issue..

Anyway, great it works.

---

