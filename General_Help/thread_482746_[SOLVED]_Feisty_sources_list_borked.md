---
title: "[SOLVED] Feisty sources list borked/"
date: 2007-06-24
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-06-24
This is not my nite for playing computer. Seems every thing I have touched has gone bad.
Would some one please look  over my sources list and assist in fixing or (oOPs) maybe fix it for me?
[B]
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
                                                                                                                       deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty exailey restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty exaile

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty exaile-svn[/B]

---

### Post by mikewhatever on 2007-06-24
What error message do you get?

---

### Post by IusedTObeSOMEONEelse on 2007-06-24
> **mikewhatever said:**
> What error message do you get?

Thanks for reply
[B]Fetched 196B in 9s (20B/s)                                                                                                 
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/Release](http://download.tuxfamily.org/syzygy42/dists/feisty/Release)  Unable to find expected entry  exailey/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]

---

### Post by r0ck80y on 2007-06-24
```
Unable to find expected entry **exailey**/binary-i386/Packages 
```
What is exailey anyway? Something is not right with the site it seems. Otherwise nothing is wrong with your sources.list file. This error wont appear when you remove  [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) deb entries from the list; unless you really need exaile.

---

### Post by IusedTObeSOMEONEelse on 2007-06-24
> **r0ck80y said:**
> ```
Unable to find expected entry **exailey**/binary-i386/Packages 
```
What is exailey anyway? Something is not right with the site it seems. Otherwise nothing is wrong with your sources.list file. This error wont appear when you remove  [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) deb entries from the list; unless you really need exaile.

Well, I was kind of excited that Exaile **FINALLY** got an equalizer!
I probly should have posted this on the thread where the 2 members (reocord or something like that name) were working on it.
Thanks for your reply ):P

---

