---
title: "GAIM updates"
date: 2005-06-04
forum: General Help
---

### Post by Gorf on 2005-06-04
I notice that the current version in Hoary is GAIM 1.1.4.  However the current version is 1.3.0 and includes some fairly solid vulnerability fixes.  I use to use the AutoPackage to install updated versions of Gaim, but now I get this error after a fresh reinstall of Hoary:

```

# Preparing: Gaim Internet Messenger
# Checking for required C library versions ... dumpverdefs: failed to find .gnu.version_d section, not a versioned Linux DSO?
failed
# FAIL:
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: .
#
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
#
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL:  Unable to prepare package Gaim Internet Messenger.


```

Try as I might, I can not get this to run.  So two questions:

1. What are people using to stay current with GAIM

2. Any ideas where my problem may lie with the autopackage?

For kicks here is uname -a:

Linux whappy 2.6.10-5-amd64-generic #1 Fri May 20 14:04:49 UTC 2005 x86_64 GNU/Linux

---

### Post by paul cooke on 2005-06-04
I'm running the 1.3.0 version from backports...

paulc@cooke-one:~$ gaim --version
Gaim 1.3.0

---

### Post by Gorf on 2005-06-04
Ok this brings me back around to a question that after using Ubuntu for like 8 months I still can't figure out... how the hell do you get backports to work?  Is there a how-to somewhere that I am missing?

---

### Post by betrayed on 2005-06-04
[QUOTE=Gorf]Ok this brings me back around to a question that after using Ubuntu for like 8 months I still can't figure out... how the hell do you get backports to work?  Is there a how-to somewhere that I am missing?[/QUOTE]
 add this to /etc/apt/sources.list
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

---

### Post by Gorf on 2005-06-04
hmmmm ok I did that, reloaded, and restarted Synaptic.  However when I search for Gaim, I am still only seeing the release version.  Same for my other apps.  Is there something unique that I have to do to get the backport version to show up?

---

### Post by derrick1985 on 2005-06-04
[QUOTE=Gorf]hmmmm ok I did that, reloaded, and restarted Synaptic.  However when I search for Gaim, I am still only seeing the release version.  Same for my other apps.  Is there something unique that I have to do to get the backport version to show up?[/QUOTE]

Gorf, try reading this:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

---

### Post by Gorf on 2005-06-04
I have read both of those before.  My question still remains:  How do I select the newer version of applications in Synaptic?  With my sources.list currently looking like this:


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

I still see no change in version numbers of applications in Synaptic.  The default example that I fall back to is Gaim.  After reloading and restarting Synaptic, the only version of Gaim that is available is 1.1.0.  That is true of other apps as well.

Is there a trick to get the backport version to override the stable version in Synaptic so I can update?

---

### Post by Xerampelinae on 2005-06-04
[QUOTE=Gorf]hmmmm ok I did that, reloaded, and restarted Synaptic.  However when I search for Gaim, I am still only seeing the release version.  Same for my other apps.  Is there something unique that I have to do to get the backport version to show up?[/QUOTE]
 I have the same problem... despite having backports added, gaim is stuck at 1.1.4

Derrick1985:  I'm not sure what information you're trying to point out... gorf said he already added backports, and your info only seems to be about how to add backports... unless there's something I'm missing?  It doesn't seem to address the problem..

---

### Post by DoomedTX on 2005-06-05
Gorf, FWIW, I was also not seeing a newer version of GAIM despite having added the backports repositories. I watched the details while the repositories were updating and saw that the mirror I was using for hoary-backports was failing. I changed to a different mirror and GAIM 1.3.0 is now available. Of course, I've already had 1.3.0 installed for some time thanks to autopackage.

---

### Post by mhearn on 2005-06-09
[QUOTE=Gorf]I notice that the current version in Hoary is GAIM 1.1.4.  However the current version is 1.3.0 and includes some fairly solid vulnerability fixes.  I use to use the AutoPackage to install updated versions of Gaim, but now I get this error after a fresh reinstall of Hoary:

```

# Preparing: Gaim Internet Messenger
# Checking for required C library versions ... dumpverdefs: failed to find .gnu.version_d section, not a versioned Linux DSO?
failed
# FAIL:
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: .
#
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
#
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL:  Unable to prepare package Gaim Internet Messenger.


```

Try as I might, I can not get this to run.  So two questions:

1. What are people using to stay current with GAIM

2. Any ideas where my problem may lie with the autopackage?

For kicks here is uname -a:

Linux whappy 2.6.10-5-amd64-generic #1 Fri May 20 14:04:49 UTC 2005 x86_64 GNU/Linux[/QUOTE]
 This is a bug in autopackage that only shows itself on AMD64 systems. Please email [email]mh@codeweavers.com[/email] your /lib/libc.so.6 file so I can take a look at it and fix dumpverdefs.

---

