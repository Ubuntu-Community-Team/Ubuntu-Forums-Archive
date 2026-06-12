---
title: "Error msg on updating package information."
date: 2008-03-03
forum: General Help
---

### Post by mk1gti on 2008-03-03
I installed 7.10 Gutsy Gibbon about 3-4 weeks ago, everything was working fine for the first couple of weeks, updating, installing software, etc. but then recently I got the error message below when updating software. Any ideas what might be causing this and how to resolve? My computer is a Toshiba laptop, 4-5 years old, Pentium 4 2.80 ghz, 512 mb ram, 80 gig hd.  Error message below, any help appreciated. Let me know if you need any additional information, still a newb at Linux. . .

Error msg on updating package information.


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 52 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by confused57 on 2008-03-03
> **mk1gti said:**
> I installed 7.10 Gutsy Gibbon about 3-4 weeks ago, everything was working fine for the first couple of weeks, updating, installing software, etc. but then recently I got the error message below when updating software. Any ideas what might be causing this and how to resolve? My computer is a Toshiba laptop, 4-5 years old, Pentium 4 2.80 ghz, 512 mb ram, 80 gig hd.  Error message below, any help appreciated. Let me know if you need any additional information, still a newb at Linux. . .

Error msg on updating package information.


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 52 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

You might want to post your sources.list:
```
gedit /etc/apt/sources.list
```

---

### Post by mk1gti on 2008-03-04
Is this what you're looking for? 

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
sudo apt-key add - && sudo apt-get update
sudo aptitude install googleearth

chmod +x ~/Desktop/GoogleEarthLinux.bin
sudo ./~/Desktop/GoogleEarthLinux.bin

---

### Post by confused57 on 2008-03-04
You need to remove the following from your sources.list:
```
sudo apt-key add - && sudo apt-get update
sudo aptitude install googleearth

chmod +x ~/Desktop/GoogleEarthLinux.bin
sudo ./~/Desktop/GoogleEarthLinux.bin
```

I assume you added them to your sources.list, but they are commands that need to be run from a terminal...to remove them:
```
cd /etc/apt
sudo cp sources.list sources.list_backup
gksudo gedit sources.list
```
remove the lines above then quit & save.

Added:  Google Earth is in the Mediubuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
this "should" be a much easier way to install it.

---

### Post by mk1gti on 2008-03-04
Thanks very much, I'll give it a try and see what happens. You've been very helpful. (^_^)

---

### Post by mk1gti on 2008-03-04
Okay, updated the info and I now have a functioning synaptic package manager again! Whoopee! Again much thanks and appreciation.

---

### Post by mk1gti on 2008-03-04
Now how do I update your 'thanks 32 in 32 posts' to 'thanks 33 in 33 posts'?

---

### Post by confused57 on 2008-03-04
> **mk1gti said:**
> Now how do I update your 'thanks 32 in 32 posts' to 'thanks 33 in 33 posts'?
Always great to hear a success story...thanks for the update.  I believe you can just click on the star in the lower right of a reply by a poster  that helped.

---

