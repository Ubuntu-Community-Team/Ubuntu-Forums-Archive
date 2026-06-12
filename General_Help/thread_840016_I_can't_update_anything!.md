---
title: "I can't update anything!"
date: 2008-06-25
forum: General Help
---

### Post by HyperHacker on 2008-06-25
No matter which server I select, every few hours I get a warning that the update info is 13 days old and it wants me to check manually. When I do I get this error, or similar ones:

> Failed to fetch [http://http.us.debian.org/debian/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.11-8_i386.deb/dists/etch/main/binary-i386/Packages.gz](http://http.us.debian.org/debian/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.11-8_i386.deb/dists/etch/main/binary-i386/Packages.gz)  404 Not Found [IP: 64.50.236.52 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Doing "sudo apt-get update" shows the same message, with this showing in the log:
> Err [http://http.us.debian.org](http://http.us.debian.org) etch/main Packages                               
  404 Not Found [IP: 64.50.236.52 80]

After doing "sudo dpkg --configure -a", I did "sudo apt-get upgrade" and it did appear to update a bunch of things, but this is still happening.

---

### Post by VMC on 2008-06-25
What does System-Administration-Software sources reflect? Ubuntu & 3rd party software.
That can also be found at "/etc/apt/sources.list"

---

### Post by perlluver on 2008-06-25
Is there supposed to be a Debian Etch repo, in there?  I thought they were all Ubuntu repos?

---

### Post by HyperHacker on 2008-06-25
/etc/apt/sources.list:
```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

#libSDL
deb http://http.us.debian.org/debian/pool/main/libs/libsdl1.2/libsdl1.2-dev_1.2.11-8_i386.deb etch main

```

---

### Post by russlar on 2008-06-25
try running **apt-get clean**, and see what that does.

---

### Post by dexter.deepak on 2008-06-25
see under system->admin->software sources ..which server are you using for downloading packages...it may be a local problem if you are using a server other than the main server.

---

### Post by eapache on 2008-06-25
The last line of /etc/apt/sources.list is the problem.

You can comment it out, (#) for now, and look at fixing it.

EDIT: I think it should be
```

deb http://http.us.debian.org/debian/pool/main/libs/libsdl1.2/ etch main

```instead.

---

### Post by HyperHacker on 2008-06-25
That wasn't it, but when I commented it, apt-get update didn't give any errors. Now I just need to see if the auto-update icon pops up with the "out of date" message again.

---

### Post by eapache on 2008-06-25
Try

```
deb http://http.us.debian.org/debian/ etch main
```

---

### Post by HyperHacker on 2008-06-26
Will that not try to install all Debian updates instead of just libSDL? :confused:

---

### Post by eapache on 2008-06-26
> **HyperHacker said:**
> Will that not try to install all Debian updates instead of just libSDL? :confused:

Yes it will. I'm not aware of a way to specify a single package in sources.list, so if you only want to use libSDL from that repo, I think it would be easier to download and install the file manually.

---

### Post by HyperHacker on 2008-06-26
OK, today it popped up saying I had 4 updates available. There were more than 4 in the list but only 4 were checked. Then it said I should do a partial upgrade, which failed with the message:> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

initscripts
libavc1394-0
sysv-rc
sysvinit-utilsAfter that, the update icon was still there, so I opened it again and declined the upgrade. When I started the update it said libavc1394-0 and sysv-rc could not be authenticated, so I unchecked those and installed the other two.

Would this have something to do with that SSL blacklisting mess a while back? Someone hasn't updated their keys?

---

### Post by eapache on 2008-06-26
Did this problem occur with the debian repo enabled or disabled?

If it occurred with the new repo enabled, my bet is that you don't have the correct authorization key. Check in System->Administration->Software Source->Authentication and see what keys you have. Ubuntu comes with two by default.

I'm pretty sure the SSL bug wouldn't have anything to do with it, but that's a bit over my head.

---

### Post by HyperHacker on 2008-06-26
I have Ubuntu Archive Automatic Signing Key (437D05B5), Ubuntu CD Image Automatic Signing Key (FBB75451) and Medibuntu Packaging Team (0C5A2783). If you mean "Debian 4.0 'Etch'", it's listed twice under Third-Party Software, one of which is enabled.

---

### Post by eapache on 2008-06-27
That's it then. Each repository you add requires a key to verify against. 

You have the two default Ubuntu keys as well as the key for the Medibuntu repos, but not the key for the Debian repo.

You should be able to install it from the Debian website.

---

### Post by HyperHacker on 2008-06-27
Will there be problems related to having Debian updates installed if I do that?

---

### Post by eapache on 2008-06-27
> **HyperHacker said:**
> Will there be problems related to having Debian updates installed if I do that?

I'm not sure. Probably.

Again, if you only need libSDL, I'd forget about using the Debian repository entirely and just download the one package via Firefox/Opera.

---

