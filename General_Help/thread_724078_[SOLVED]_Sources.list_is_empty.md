---
title: "[SOLVED] Sources.list is empty"
date: 2008-03-14
forum: General Help
---

### Post by portach king on 2008-03-14
Hey,
So I noticed a few weeks ago that the regular updates I was used to getting had slowed down and that I wasn't getting any daily update notifications anymore, but to be honest it didn't bother me much and I didn't think much of it. However today I opened up the terminal and used gedit to add a link to sources.list and to my surprise I found that it's a completely blank document. I found sources.list.save does have all the previous information that sources.list should have, however when I tried to copy & paste that info over into sources.list document I get a message that reads "Could not Save. Unexpected Error. File not found"
In Terminal:
```
** (gedit:3735): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
```

I can see sources.list does exist though, it's just completely empty.
I'd appreciate any help. Thank you.

---

### Post by handydan918 on 2008-03-14
> **portach king said:**
> Hey,
So I noticed a few weeks ago that the regular updates I was used to getting had slowed down and that I wasn't getting any daily update notifications anymore, but to be honest it didn't bother me much and I didn't think much of it. However today I opened up the terminal and used gedit to add a link to sources.list and to my surprise I found that it's a completely blank document. I found sources.list.save does have all the previous information that sources.list should have, however when I tried to copy & paste that info over into sources.list document I get a message that reads "Could not Save. Unexpected Error. File not found"
In Terminal:
```
** (gedit:3735): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
```

I can see sources.list does exist though, it's just completely empty.
I'd appreciate any help. Thank you.

In a terminal, do ```
cd /etc/apt
```
Then, ```
sudo, mv sources.list.save sources.list
```That should rename the backup file to the working sources.list

---

### Post by portach king on 2008-03-14
Ugh. My stomach just turned.
No that didn't help, Sources.list is still empty and now Sources.list.save is gone....

:confused:

---

### Post by PmDematagoda on 2008-03-14
Open Software Sources in System>Administration>Software Sources and enable the required options, after that is done, close the window and reload the sources list, after that is done recheck the sources.list file.

---

### Post by portach king on 2008-03-14
All the boxes inside Software Sources are checked

---

### Post by PmDematagoda on 2008-03-14
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by portach king on 2008-03-14
All I'm getting in Terminal is
```
cat: /etc/spt/sources.list: No such file or directory
```

Thank for your help by the way, this is hugely appreciated

****EDIT****

Wait, sorry. There are my sources:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb http://apt.wicd.net gutsy extras

```

---

### Post by PmDematagoda on 2008-03-14
> **portach king said:**
> All I'm getting in Terminal is
```
cat: /etc/spt/sources.list: No such file or directory
```

Thank for your help by the way, this is hugely appreciated

****EDIT****

Wait, sorry. There are my sources:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb http://apt.wicd.net gutsy extras

```

Sorry about the first command, there was a typo.

But for the correct command, your sources list is full, what is the problem?

---

### Post by portach king on 2008-03-14
Well, when I still try and open sources.list via gedit it stil appears as empty...

---

### Post by PmDematagoda on 2008-03-14
Was the command:-
```
gedit /etc/apt/sources.list
```

---

### Post by tad1073 on 2008-03-14
> **portach king said:**
> Well, when I still try and open sources.list via gedit it stil appears as empty...
You need to sudo the command.

---

### Post by portach king on 2008-03-14
OK, it's working now.. I just realized what I was doing wrong. I was typing:
sudo gedit etc/apt/sources.list
instead of:
sudo gedit /etc/apt/sources.list

I'm sorry (and extremely embarrassed), and thank you for all the help. If nothing else it was extremely educational.

:)

---

### Post by PmDematagoda on 2008-03-14
> **tad1073 said:**
> You need to sudo the command.

Only to edit the file, you can still view it without sudo.

---

### Post by PmDematagoda on 2008-03-14
> **portach king said:**
> I'm sorry (and extremely embarrassed), and thank you for all the help. If nothing else it was extremely educational.

:)

No worries, you learn by doing mistakes, so don't be embarrassed:).

---

### Post by tad1073 on 2008-03-14
> **PmDematagoda said:**
> Only to edit the file, you can still view it without sudo.
My mistake.

---

