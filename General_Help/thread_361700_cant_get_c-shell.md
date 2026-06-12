---
title: "cant get c-shell"
date: 2007-02-14
forum: General Help
---

### Post by Barry T on 2007-02-14
Jeez! After reading dozens of posts about other users getting csh from the repositories, I still cant get it. This includes managing the repositories in Adept. Why is it so hard to d/l csh? Synaptic can't find it either. Help!:

---

### Post by finer recliner on 2007-02-14
correct me if i'm wrong, but isn't tcsh the latest build off of csh (making csh obsolete)? try installing that.

---

### Post by llamakc on 2007-02-14
Be certain you have universe enabled, and be sure to reload your sources.list. I don't know how to do that in Synaptic/Adept. In the terminal it is:

sudo apt-get update

then, apt-cache show csh

Package: csh
Priority: optional
Section: universe/shells
Installed-Size: 384
Maintainer: Matej Vela <vela@debian.org>
Architecture: i386
Version: 20060413-1
Provides: c-shell
Depends: libc6 (>= 2.4-1)
Filename: pool/universe/c/csh/csh_20060413-1_i386.deb

---

### Post by Barry T on 2007-02-15
Hi, guys! Thanks for trying to solve my problema. Hey, finer recliner, my sudo apt-get install tcsh could not find that one, either, although I have seen references to it on the various posts in this forum. And, llamakc, the sudo apt-get install update generated about 20 lines of output, but the apt-cache show csh gave two lines. W: Unable to locate package csh, and E: No packages found. This is wierd! Any more ideas? Thanks again!

---

### Post by taurus on 2007-02-15
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Barry T on 2007-02-15
Hi,guys! Here it is. Thanks!

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer                        se multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un                        iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
barrykubuntu@alien:~$

---

### Post by llamakc on 2007-02-15
Use this:

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe


```

Re-run `sudo apt-get update` and then `sudo apt-get install csh`

---

### Post by lamego on 2007-02-15
If you look at your file instead of just copying you will notice that the "universe" entires are commented (#).

---

### Post by llamakc on 2007-02-15
> **lamego said:**
> If you look at your file instead of just copying you will notice that the "universe" entires are commented (#).

And perhaps they would realize that they only have universe commented out for edgy-backports (where there is an error in a space in the middle of the word) and edgy-security. There is no mention of universe anywhere else.

```

 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer                        se multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un                        iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


```

OP: you need to fix your sources.list. You can either edit it yourself or use Synaptic/Adept to alter it.

---

### Post by Barry T on 2007-02-15
Hi, guys! Success! Correcting the urls allowed me to find, d/l and install csh. Many thanks! I never would have guessed that was the problem--still a noobie. I did not un-comment out the appropriate text, because I use Adept to manage the repositories. And it was grayed-out in Adept, so I figured I didn't need to un-comment it. Thanks again.

---

