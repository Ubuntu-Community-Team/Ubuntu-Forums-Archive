---
title: "[SOLVED] Autoamitx installer give error message."
date: 2007-10-28
forum: General Help
---

### Post by burritomaster on 2007-10-28
So I've upgraded to Gusty, and want to install Autoamtix again because its the easiest way to install software. I downloaded the deb file from the Automatix site, ran it, and I get the message "Error: Dependency is not satasfiable: tango-icon-theme-common." Its a clean install and the only thing I've modified about the system, is the theme which I downloaded from the internet. The theme is called moomtex if it makes a differences. Any thoughts about the error message?

---

### Post by ThrobbingBrain66 on 2007-10-28
Have you tried to install the package?
```
sudo apt-get install tango-icon-theme-common
```

This works for me.  If it doesn't for you, post your sources.list file

```
cat /etc/apt/sources.list
```

I'll save you the speech on using Automatix...I'm sure you've heard it numerous times already. :)

---

### Post by burritomaster on 2007-10-28
Yeah, I've know the speech. I just don't have the time to mess with terminal, and compile the source code. I know that it screw with the upgrades, but I prefer a clean install anyway. The sources.list is in bold.

[B]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free [/B]

---

### Post by ThrobbingBrain66 on 2007-10-28
I'd be surprised if you had to do anything with the terminal or compiling.  The vast majority of packages are in the repos and 3-4 simple clicks away.  Anyway, your entire sources.list has been commented out....this is proably why you haven't recieved any updates since the Gutsy release.

Use my list instead....it's the same as yours, just cleaned up a lot.

```

## Main & Restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Universe & Multiverse                                                   
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse universe

## Bug Fixes
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse universe

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted multiverse universe

## Security Updates
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse universe

## Proposed Updates
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted multiverse universe

## Canonical Partner
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

```

---

### Post by burritomaster on 2007-10-28
That did the trick. Copied your sources.list, update the OS, then ran the Automatix deb. Thanks.

---

### Post by Crafty Kisses on 2007-10-28
> **ThrobbingBrain66 said:**
> Have you tried to install the package?
```
sudo apt-get install tango-icon-theme-common
```

This works for me.  If it doesn't for you, post your sources.list file

```
cat /etc/apt/sources.list
```

I'll save you the speech on using Automatix...I'm sure you've heard it numerous times already. :)

You should always try installing the package, try not to use Automatix.

---

### Post by EXCiD3 on 2007-10-28
At least with the new automatix that will be released they are working closely with the developers meaning that it WILL work appropriately and won't break things.

---

