---
title: "Help with Synaptic"
date: 2008-02-24
forum: General Help
---

### Post by natibo on 2008-02-24
Synaptic will no longer load.  I get the following error:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


How can I correct this ASAP!!!!!!!

I am a newbie.

---

### Post by LuisGMarine on 2008-02-24
Sounds like you  sources list can be messed up.

Try this:

```
 sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup   
```
```

sudo gedit /etc/apt/sources.list
```

and remove everything inside, and copy and paste this into it. 


```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```


Save the file and quit, then run

```
sudo apt-get update
```

*** note this rep list includes the extra backports and stuff, the non-free to sort of speak.  I don't think they can dmg your system, but someone correct me if I'm wrong.  About 99.9% of people enable them anways.

---

### Post by plucky on 2008-02-25
> Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

The problem is in the **medibuntu.list** file ,not the **sources.list** file ```
cat /etc/apt/sources.list.d/medibuntu.list
``` and you should find the word **!DOCTYPE'** in line 1.
You will need to edit this file,but first make a copy with ```
cp  /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.backup
``` Then ```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
``` and comment out the **!DOCTYPE** in line 1 by putting a **#** in front of it.

Good luck

---

