---
title: "Partial upgrade involving GIMP...?"
date: 2008-07-07
forum: General Help
---

### Post by MEGAMANULTIMATE on 2008-07-07
Dear all Ubuntuphiles,

I own a Dell M1210 laptop and I haven't installed anything recently, or added any 3rd party repositories. I got a notice in my latest update about a "Partial Upgrade," or something to that effect. I only ask if this is something I should go through, because looking at other posts of this subject have got me spooked. I've included two screenshots with the message, and the packages that will be installed if I followed through with the upgrade. Any feedback at all would be greatly appreciated.


P.S.- I understand that "Ubuntuphiles" is probably lame...I just wanted to try it out.

---

### Post by MEGAMANULTIMATE on 2008-07-08
bump

---

### Post by mcduck on 2008-07-08
Instead of using the Update Manager try updating with Synaptic. It's able to handle certain situations that the Update maanger isn't allowed to handle (like updates that require uninstalling some package, for example).

---

### Post by forger on 2008-07-08
1) Are you using gutsy gibbon 7.10?

2) You have backports enabled, you should disable them, they're not stable
 a) Go to System > Administration > Software Sources > Updates > make sure you have **[COLOR="Red"]unchecked[/COLOR]** the **-proposed** and **-backports**
b) Also make sure in Software Sources > Ubuntu Software than you have unchecked anything that mentions backports.
c) Then click "Close" and "Reload"
d)
Can you open Applications > Accessories > Terminal and post back the output of:
```
cat /etc/apt/sources.list
```

---

### Post by Olav on 2008-07-08
> **MEGAMANULTIMATE said:**
> P.S.- I understand that "Ubuntuphiles" is probably lame...I just wanted to try it out.
Actually, we're Ubuntunistas :mrgreen:

---

### Post by MEGAMANULTIMATE on 2008-07-08
matthew@matthew-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

#AUTOMATIX REPOS END
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main


My sources.list. Do you know how to post that terminal-text window thing? I can't seem to get it working....I also disabled backports and now there is no update at all. Crossing fingers for great justice!

---

### Post by forger on 2008-07-08
1) If you want newer software, you better upgrade to hardy, best way to get the newest stable versions :)
2) Ditch automatix, it tends to break stuff

Let's remove automatix, do:
```
sudo aptitude purge automatix automatix2
```

Now let's edit sources.list:
```
gksu gedit /etc/apt/sources.list
```

in the text editor, clear the file, and add the following:
> 
#software
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

#security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

#updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main


save the file and close the text editor.

Now do:
```
sudo apt-get update
sudo apt-get autoclean
sudo apt-get upgrade
```

---

### Post by MEGAMANULTIMATE on 2008-07-08
Thanks forger, I'll definitely follow the steps you gave. One question: How does automatix break stuff? I don't mean to pry, I just never knew that it did.

Thanks so much!

---

