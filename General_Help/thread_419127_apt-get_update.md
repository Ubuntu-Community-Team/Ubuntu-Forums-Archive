---
title: "apt-get update"
date: 2007-04-22
forum: General Help
---

### Post by ryantmer on 2007-04-22
Whenever I run apt-get update from the shell, and it goes through the checking, it eventually hangs up on "99% [Waiting for headers]"... there is also no download speed shown. I thought initially it was just slow, but sure enough, hours later, it is still like this. I also tried updating it from Synaptic, but it goes through a whole bunch, and gets caught after "archive.ubuntu.com feisty-security/multiverse Packages". -.-

Any ideas? I'm thinking there's something wrong with my sources.list, but I don't know where to start...

---

### Post by hikaricore on 2007-04-22
What have you added to your sources.list file? 

Sometimes unsupported repos go down and this can cause your apt-get update
to stop responding or take longer as it waits for the server to time out.

You might want to post the contents of /etc/apt/sources.list here

---

### Post by ryantmer on 2007-04-22
My sources.list file... prolly kinda messy, I've been fiddling with it a lot. Hell, I think I have duplicates in some cases.


deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) feisty free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) feisty free non-free

deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) feisty free non-free
deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main restricted multiverse

#ntfs-3g & fuse-2.5 repo
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) feisty main
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) feisty main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main oprestricted
#ntfs-3g repo deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/)  feisty main main-all

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by jfinkels on 2007-04-22
Check out this line... probably you want "restricted" and not "oprestricted"
```
deb http://security.ubuntu.com/ubuntu/ feisty-security universe main oprestricted
```

---

### Post by ryantmer on 2007-04-22
Did that... but now I get a message that says:

"E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory"

-.-"

---

### Post by jfinkels on 2007-04-22
That most likely means youre trying to run two instances of aptitude or Synaptic or something like that. Make sure you close Synaptic before running aptitude or apt-get!

---

### Post by ryantmer on 2007-04-22
>.<

Fixed that, that was indeed the problem. But I still have the problem with apt-get update...

Here is my new sources.list, I changed it a bit (mostly changed it back to default):

## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## cae the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity caing 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to cae the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to cae the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide caeful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  cae at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

#AUTOMATIX REPOS START
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by jfinkels on 2007-04-22
> **ryantmer said:**
> >.<

Fixed that, that was indeed the problem. But I still have the problem with apt-get update...

Here is my new sources.list, I changed it a bit (mostly changed it back to default):


A couple things:

1. when you post the contents of files or code or something like a long listing, use the <CODE></CODE> tags to make the output look
```

like this.

```
At the top of the message editor when you make a post, there's a button with a hash ("pound") symbol on it which inserts code tags.

2. Can you tell which address apt-get actually gets stuck on/after? Please post it here if possible.

---

### Post by ryantmer on 2007-04-22
Oh, yeah, code tags... Forgot those existed XD

Seems to be fixed, it now only hangs up for a bit after one of the lines (Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/multiverse Packages), then continues. But when it doesn't hang, I get this at the end of the check cycle:

```
W: GPG error: http://deb.opera.com etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
```

And no matter how many times I do apt-get update, I still get the same thing...

Rawr.

---

### Post by zvacet on 2007-04-23
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key ad[/B]


and in your case

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 033431536A423791
 gpg --export --armor 033431536A423791  | sudo apt-key ad

do the same with second one

---

### Post by jfinkels on 2007-04-23
> **zvacet said:**
> [B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key ad[/B]


and in your case

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 033431536A423791
 gpg --export --armor 033431536A423791  | sudo apt-key ad

do the same with second one

I think it should be 
```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 033431536A423791
gpg --export --armor 033431536A423791  | sudo apt-key **_*add*_**

```
Two Ds for "add" :)

---

### Post by ryantmer on 2007-04-23
Receiving the keys works fine, but when I try to run the second line (with "add"), I get ```
gpg: can't open `': No such file or directory
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error
```

*blink*

---

### Post by jfinkels on 2007-04-23
> **ryantmer said:**
> Receiving the keys works fine, but when I try to run the second line (with "add"), I get ```
gpg: can't open `': No such file or directory
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error
```

*blink*

Okay check this out: I missed another mistake! The line should look like this:
```

gpg --export --armor 033431536A423791  | sudo apt-key add -

```
Note the dash at the end (that signifies that "apt-key add" is going to be receiving input which is the output of another program, basically).

---

### Post by ryantmer on 2007-04-25
A-ha! Worked perfectly, thanks :)

---

### Post by brigade on 2007-04-29
Ahh awesome thank you for the fix this fixed my problem once I realized that I actually had to put the key number in there. I am pretty new to the GPG thing so you helped alot thanks.

V/R,
Brig

---

### Post by hellblade on 2007-05-03
hmmm ignore that msg

---

