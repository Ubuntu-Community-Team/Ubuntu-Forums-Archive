---
title: "Kubuntu Updates"
date: 2005-11-02
forum: General Help
---

### Post by kaptainlange on 2005-11-02
So just to be sure, have there been any updates released yet for any of kubuntu's default software.  Back when I was using ubuntu I noticed I'd get updates nearly every day for miscellaneous stuff, but with Kubuntu I haven't had to update at all since I installed.

Kind of hoping things like the wireless networking configurators, etc will get updates and work like they should.  Or do I have something misconfigured.

---

### Post by Princey on 2005-11-02
How long ago did you instal kubuntu? Up to yesterday I did a check and there were updates, one covered a problem I had with mounting ntfs partitions. Either use adapt update manager or type in at the terminal:

sudo apt-get update

You should see a set of updates if you installed kubuntu breezy just after it was released. To install the updates, type in at the terminal prompt:

sudo apt-get install


Good luck

---

### Post by kaptainlange on 2005-11-02
I'd say its been about two-three weeks since I installed.  I've been checking adept-updater, but haven't had an update yet.  I do recall an update back when I installed, but I wouldn't be able to remember what it was.

Mainly was just curious if they've released any fixes for some of the config tools they have on here.  Tired of editing my interfaces file.

---

### Post by jeremy on 2005-11-02
Please post a copy of your /etc/apt/sources.list

---

### Post by kaptainlange on 2005-11-02
```
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted multiverse

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

# keys for verification are retrieved with gpg:
# gpg --recv-keys 07DC563D1F41B907
# and added with apt-keys:
# gpg --export -a 07DC563D1F41B907 | sudo apt-key add -
# (the example is Christian Marillat’s key)
#deb ftp://ftp.nerim.net/debian-marillat/ sarge main

#deb http://splashy.alioth.debian.org/debian unstable main 

```

There ya go.

---

### Post by jeremy on 2005-11-02
Hmmm. looks fine to me.
have you tried:
sudo apt-get clean
followed by:
sudo apt-get update
then:
sudo apt-get upgrade

If that doesn't work you could try going through you sources.list and removing the 'us.' from each entry, but I doubt if that is the problem.

---

### Post by kaptainlange on 2005-11-02
Followed those commands, and no upgrades where available, I may just be currently updated.  How often should I expect any kind of updates.  Like I said with Ubuntu it seemed like everyday a miscellaneous update would come out, but nothing of that kind now.

---

### Post by shinygerbil on 2005-11-02
There haven't been many updates recently; I hit update every day just in case, but nothing happens. I guess Kubuntu's just up-to-date... Sure wish they'd fix a few things though

Steve

---

### Post by jeremy on 2005-11-02
I remember that shortly after I installed breezy, there was an update for kdebase (among others) to version 4:3.4.3-0ubuntu5
So look and see if that is the version you have, an if so, then you are presumerably up to date.

---

### Post by ecobuntu on 2005-11-02
[QUOTE=Princey]How long ago did you instal kubuntu? Up to yesterday I did a check and there were updates, one covered a problem I had with mounting ntfs partitions. Either use adapt update manager or type in at the terminal:

sudo apt-get update

You should see a set of updates if you installed kubuntu breezy just after it was released. To install the updates, type in at the terminal prompt:

sudo apt-get install


Good luck[/QUOTE]

Howdy Mr. Speedy-
You're half right...
sudo apt-get update
sudo apt-get upgrade

cheers

---

### Post by Princey on 2005-11-03
[QUOTE=ecobuntu]Howdy Mr. Speedy-
You're half right...
sudo apt-get update
sudo apt-get upgrade

cheers[/QUOTE]
Thanks for the correction:KS , it's always a learning process.

It may worth mentioning that while there are a few things worth fixing in breezy, it's doubtful that updates would roll out everyday. If you want to see something fixed, it sure worth filing a bug report especially if there are a few posts already on your "broken" issues you may be having.

---

