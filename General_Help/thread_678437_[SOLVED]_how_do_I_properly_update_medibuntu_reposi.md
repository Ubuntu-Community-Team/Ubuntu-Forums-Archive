---
title: "[SOLVED] how do I properly update medibuntu repositories?"
date: 2008-01-25
forum: General Help
---

### Post by malrost on 2008-01-25
Hm. I've tried the "adding the repositories" commands on the medibuntu wiki, and haven't found anything in the ubuntu forums on this.

On  Gutsy/7.10 install, I ran into the following error when running 'check' on the update manager.


[INDENT]"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.medibuntu.org/dists/gutsy/free/binary-amd64/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/free/binary-amd64/Packages.gz:) 301 Moved Permanently [IP: 88.191.30.43 80]
[http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages.gz:) 301 Moved Permanently [IP: 88.191.30.43 80]"
[/INDENT]

The following command gives me no results
```
grep medibuntu /etc/apt/sources.list

```

...and here are the results of  ```
sudo apt-get update | grep medibuntu
```

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsy/free/binary-amd64/Packages.gz)  301 Moved Permanently [IP: 88.191.30.43 80]
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-amd64/Packages.gz)  301 Moved Permanently [IP: 88.191.30.43 80]
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any idea how to fix this? Thanks.

---

### Post by wolfen69 on 2008-01-25
post the results of
```
cat /etc/apt/sources.list
```

---

### Post by jfgordon on 2008-01-26
I've got the same problem with medibuntu going, and this is what my sources list looks like.  As far as I can tell, nothing looks wrong.

```

## -----------------------                                   
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Daryna (Linux Mint 4.0) +++
deb http://www.linuxmint.com/repository daryna main upstream import
## deb http://www.linuxmint.com/repository daryna community
## deb http://www.linuxmint.com/repository daryna backport

## +++ Romeo (Linux Mint Unstable) +++
## deb http://www.linuxmint.com/repository romeo daryna

## +++ Source Repositories +++
## deb-src http://www.linuxmint.com/repository daryna main upstream import
## deb-src http://www.linuxmint.com/repository daryna community
## deb-src http://www.linuxmint.com/repository daryna backport
## deb-src http://www.linuxmint.com/repository romeo daryna

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Gutsy (Ubuntu 7.10) +++
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

## +++ Backports & Proposed (Ubuntu Unstable) +++
# deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

## +++ Source Repositories +++
# deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical +++ 
deb http://archive.canonical.com/ubuntu gutsy partner

## +++ Medibuntu +++
deb http://packages.medibuntu.org/ gutsy free non-free

## +++ Canonical +++
deb http://us.archive.ubuntu.com/ubuntu gutsy universe
deb http://wine.budgetdedicated.com/apt gutsy main
deb http://archive.ubuntu.com/ubuntu gutsy-proposed restricted main multiverse universe

```

---

### Post by malrost on 2008-01-26
as requested by wolfen69, the results of ```
cat /etc/apt/sources.list
```


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
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

---

### Post by PeterJS on 2008-01-26
I just tired updating my sources after seeing this thread, and the first couple times it didn't work, but it looks like they're back now. Try giving it another go and seeing what happens.

EDIT

And now it's broken again :(

---

### Post by malrost on 2008-01-26
PeterJS -- just tried it again, and got the same error.

I don't see a prior mention from you -- were you getting the same error before too?

---

### Post by PeterJS on 2008-01-26
It's broken again. I must have just gotten lucky there. I've seen a couple threads about this, I'm thinking it's a breakage on their end.

Ok I just tired twice more, the first time worked but not the second.

---

### Post by malrost on 2008-01-26
Ah, so it sounds like it *actually is* a network error on medibuntu.org's end. It seemed unlikely to me, but I will take your prior success as a confirmation and mark this one as solved. Thanks for your help!

---

### Post by ProsperB on 2008-01-26
Well, it's easy to mark Solved, but it ain't finished yet. Remark it does say "moved permanently". Trying to access [www.medibuntu.org](www.medibuntu.org) I got all kinds of warnings about certificates not belonging to medibuntu.  Following up on those I came to an external host service for medibuntu repositories: some French guy named Dunnewind..  The least one can say is that  it is weird.  Can someone dig this out ?

---

### Post by malrost on 2008-01-26
I'm sorry -- do you suggest I mark it as 'unsolved'? The concern of this thread was the update manager, and intermittent medibuntu network issues work for me.

I certainly appreciate your skepticism --nothing wrong with erring on the side of being secure-- but the GPG public key does work, after all. Which, if I understand the PGP upon which it is based properly, means that anyone attempting to substitute malicious code into the repository would need to have the private key.

While mine eventually worked, there were no updates. I understand your concern but do not share your suspicion. Still, please do let me know if you dig anything up.

---

### Post by ProsperB on 2008-01-26
Maybe suspicion is not the exact word to describe my feelings, though some of it does creep up...
Your remarks about the key are reassuring, thank you.  
It is rather that, a couple of months ago, medibuntu changed its repositories from something like "medibuntu.sos-cm.org" (I know this isn't the exact way it was) to packages.medibuntu.org (which I know to be correct). This caused all kinds of petty problems because tutorials and howto's weren't updated and people, especially new users, kept hitting the walls.

If, and I repeat if, this is a second time around that medibuntu is moving its repositories, the least we can say is that their communication is singularly lacking in clarity.
But we'll wait out for a couple of hours.  I posted a thread on the Dutch forum, so people there will start trying to see what's going on.  If something useful comes up, I'll let you know.

---

### Post by peter23 on 2008-01-26
```
$ wget --spider http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz
--11:29:23--  http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz
           => `Packages.gz'
&#1047;&#1072;&#1087;&#1088;&#1086;&#1089; &#1087;&#1086;&#1089;&#1083;&#1072;&#1085;, &#1086;&#1078;&#1080;&#1076;&#1072;&#1085;&#1080;&#1077; &#1086;&#1090;&#1074;&#1077;&#1090;&#1072;... 301 Moved Permanently
&#1040;&#1076;&#1088;&#1077;&#1089;: https://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz [&#1087;&#1077;&#1088;&#1077;&#1093;&#1086;&#1076;]
--11:29:24--  https://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz
           => `Packages.gz'
...
```

http**S**
apt-get doesn't process HTTP-redirects and also is not able download through https, at least at me

**added**
Install a package apt-transport-https
# apt-get install apt-transport-https
replace
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free
```
on
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb https://packages.medibuntu.org/ gutsy free non-free
deb-src https://packages.medibuntu.org/ gutsy free non-free
```
in/etc/apt/sources.list
```
# apt-get update
```
But there is a problem with SSL-certificates.

---

### Post by ProsperB on 2008-01-26
Thanks for your reply.  I didn't follow it, since they're back to "normal".  Must have been network related, as stated before.  Still believe it's weird, though...

---

