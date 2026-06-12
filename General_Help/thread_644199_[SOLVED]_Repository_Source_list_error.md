---
title: "[SOLVED] Repository Source list error"
date: 2007-12-18
forum: General Help
---

### Post by Bugsy969 on 2007-12-18
Hi i'm kind of new at Linux ( aka Ubuntu 7.10 Gusty ) i'm been teaching my self and it's been working out pretty good...but somthing came up, 

it will not alow me to open my synaptic package manager anymore it comes up with an error :

E: Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

so i went to the sorce list and tryed a couple things to see if i could get it working but in the end i just got more error codes :

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

E: Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list
E: Unable to lock the list directory

E: Type 'sudo' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i'd really apreciate it if i could get some assistance, like i said i'm kinda new so i'm stumped on what's going on or how to fix it thnx 
Bugsy.

---

### Post by forestpixie on 2007-12-18
ok - open a terminal - Apps> accessories>terminal

paste this in, enter copy and paste the output here please

```
cat /etc/apt/sources.list
```

---

### Post by Bugsy969 on 2007-12-18
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
sudo apt-key add -
sudo apt-get update
echo "deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main"
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-
sudo apt-key add -
sudo apt-get update
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

---

### Post by Bugsy969 on 2007-12-18
i also wanted to add... i can't even unpack .deb files.. this error comes up :

Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by Bugsy969 on 2007-12-18
if too it is any help i can probibly find the code i typed in when i first got the error.

---

### Post by forestpixie on 2007-12-18
ok - open the file for editing 
```
gksudo gedit /etc/apt/sources.list
```

if you're doing things to files and you want to back up before you start, use this command ;)
```
cp path/to/file /path/to/backup
```

eg
```
cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
but no need here - you've got a copy here for eternity:)

at the bottom of the file delete these lines

> sudo apt-key add -
sudo apt-get update
echo "deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main"
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-
sudo apt-key add -
sudo apt-get update
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main 

you might also want to stop apt looking at the cdrom - to do that delete the lines from the beginning
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
```

save and close the file

in terminal do this to make sure that all is ok 

```
sudo apt-get update
```

if that is ok in terminal do this which is what you were trying to do in the first place from the rowdy server I hope - enter after each command, if you get a problem before adding these post it

```
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list 
```

```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add - 
```

```
sudo apt-get update
```

---

### Post by forestpixie on 2007-12-18
all connected I hope

---

### Post by Bugsy969 on 2007-12-18
K i'll try it out, but yeah i was on 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Playstation_Emulator_.28pSX.29_1.13_for_i386.2FAMD64](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Playstation_Emulator_.28pSX.29_1.13_for_i386.2FAMD64)

trying to install a  Playstation Emulator (pSX) 1.13 for i386

and this is what i put: 

echo "deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main" | sudo tee -a /etc/apt/sources.list
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install psx

but somwhere inbetween the code it came up with that error.

any way i'll try this out and see how it goes :) thanks for the help

---

### Post by forestpixie on 2007-12-18
ok well I did the same and all worked properly here - so go through do each one separately and we should get there

---

### Post by Bugsy969 on 2007-12-18
I must say i've been a windows ( GUI ) person all my life....but..

Ubuntu.... truelly a work of art...

Thank you vary much everything is working Amazing.

Will post again if i have any problems in the future :)

---

### Post by forestpixie on 2007-12-18
cool glad I could help I'm off to count sheep 

can you mark thread solved - :D

---

### Post by Bugsy969 on 2007-12-18
done

---

