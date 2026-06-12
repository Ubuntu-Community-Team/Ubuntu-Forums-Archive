---
title: "[SOLVED] Yet another Could not download all repository indexes"
date: 2007-10-30
forum: General Help
---

### Post by twd09 on 2007-10-30
I've gone through all the other threads and thusfar none of the solutions listed therein worked for me. Regardless of what server I choose I get the dreaded Could not download all repository indexes error (malformed release file?). If I copy and paste the failed URL's into firefox I can access them with no problems however. In fact once when I did that I Update Manager detected an update for wine and downloaded and install it with no problems. I've tried disabling my firewall, hooking directly into the broadband connection and still the same problem which leads me to believe theres some software setting I'm missing. It did this once before about 6 days ago and changing the repositories to something and then back somehow made it work but since then I've been stuck. If I try to install any program via Add/Remove I get 

> XXXXXX cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

Any help would be greatly appreciated

---

### Post by twd09 on 2007-10-30
if I run sudo apt-get update this is what is returned:

```
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/web Translation-en_US
Ign http://security.ubuntu.com gutsy-security/web Translation-en_US
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/web Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Fetched 4B in 0s (5B/s)  
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by taurus on 2007-10-30
_WHY_ do you have both Feisty and Gutsy repos in /etc/apt/sources.list at the same time?

Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

p.s.  Are you running Gutsy right now?

---

### Post by twd09 on 2007-10-30
```
#AUTOMATIX REPOS END
# deb http://www.ansemreport.com/pidgin/repo feisty feisty-backports
deb http://security.ubuntu.com/ubuntu/ gutsy-security web multiverse restricted universe main
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main web universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates web multiverse restricted universe main
```

Yes, running Gutsy right now but had upgraded from Feisty. I just rebuilt my sources list but had done it several times. I probably cut and pasted a few too many solutions and didn't notice but now my sources.list file doesn't include any Feisty entires - stil the same problem though

---

### Post by twd09 on 2007-10-31
*mild bump*

---

### Post by twd09 on 2007-11-01
bump

---

### Post by taurus on 2007-11-01
You can keep bumping your thread if you wish but why don't you just include your /etc/apt/sources.list!  Is it a top secret or something?

```
cat /etc/apt/sources.list
```

---

### Post by twd09 on 2007-11-01
Issue resolved

---

### Post by Maestro23 on 2007-11-01
> **twd09 said:**
> Issue resolved

Please mark this SOLVED using the Thread Tools.

Could also include what you did to resolve the situation, as it may help people in the future with a similar issue.

---

### Post by twd09 on 2007-11-01
I really can't say what solved it, about 60 hours ago Add/Remove programs finally was able to retrieve its list. After doing nothing for 24 hours update finally retrieved its list of programs, updated but then went back to not working. Clearing out sources.list and and then resetting software sources seemed to make it work. However trying the same thing 2 days ago had no affect.

---

### Post by mikeg008 on 2008-01-03
I had this same issue.  Removing "web" from /etc/apt/sources.list worked instantly for me.  I am running a fresh install of Edubuntu/Mythbuntu.
Here is my  /etc/apt/sources/list

###########################################
## Change Log:
## 1-3-2007--> "web" is removed from 3 lines below because "apt-get update"
##  does not work with it there.
##
##
###########################################
deb cdrom:[Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# "web" is removed from the line below because "apt-get update"
# does not work with it there.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# "web" is removed from the line below because "apt-get update"
# does not work with it there.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
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
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# "web" is removed from the line below because "apt-get update"
# does not work with it there.
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted web
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
## Mike's additions
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by jKeats3 on 2008-03-22
Ditto...I had the same issue.   I just commented out every place it said "web" at the end of an apt line, and now I'm not getting any errors.  I don't really know anything about this, but I wonder what "software-properties" is.  Basically everwhere I had a problem, there was a comment that said, "#added by software-properties", so I'm thinking that whatever "software-properties" program or function is, that is the root cause of this problem.


Working /etc/apt/sources.list file:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted #web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse #web universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted #web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse #web universe #Added by software-properties

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
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted #web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse #web universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
# deb [http://ppa.launchpad.net/ruben/ubuntu](http://ppa.launchpad.net/ruben/ubuntu) gutsy main
# deb [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) gutsy main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
# deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
# deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main

---

### Post by ricanelite on 2008-04-05
now im wondering when im upgrade to my hardy when it releases. What is going to happen? Are we going to have to take out all the Gusty respos from the sources.list?

---

