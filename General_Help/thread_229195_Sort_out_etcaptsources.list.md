---
title: "Sort out /etc/apt/sources.list"
date: 2006-08-04
forum: General Help
---

### Post by Lunar_Lamp on 2006-08-04
I have messed around a lot with my sources list in the past, and at some point I've added a duplicate.  I think it's to do with me not understanding how the differentiation works for universe and multiverse etc in the file.  Could someone show me what I can delete from my sources list please:

```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## used for Listen, Just Listen
deb http://theli.free.fr/packages/ dapper listen

## Bibus
# deb http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
# deb-src http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

## cinelerra
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./

## wine
deb http://wine.budgetdedicated.com/apt dapper main

## added for amarok
deb http://kubuntu.org/packages/amarok-14 dapper main

##added for xgl/compiz as per http://tazforum.thetazzone.com/viewtopic.php?t=2189
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main


##added for gaim 2.0 as per http://ubuntuforums.org/showthread.php?t=204523
# deb-src http://ftp.uk.debian.org/debian unstable main contrib non-free
# deb-src http://ftp.uk.debian.org/debian experimental main contrib non-free

```

---

### Post by scxtt on 2006-08-04
you can get rid of any single entry if it's also listed in another entry w/ multiple sections, for example:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

takes care of:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main multiverse

---

### Post by Ramses de Norre on 2006-08-04
I made a more easy sources.list for you, I also added the PLF repo for dapper, your version was still breezy. Comment it if you don't like it. You can also add the gb. part if you like.
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## Dapper PLF repository
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

## used for Listen, Just Listen
deb http://theli.free.fr/packages/ dapper listen

## Bibus
# deb http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
# deb-src http://easynews.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

## cinelerra
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./

## wine
deb http://wine.budgetdedicated.com/apt dapper main

## added for amarok
deb http://kubuntu.org/packages/amarok-14 dapper main

##added for xgl/compiz as per http://tazforum.thetazzone.com/viewtopic.php?t=2189
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main


##added for gaim 2.0 as per http://ubuntuforums.org/showthread.php?t=204523
# deb-src http://ftp.uk.debian.org/debian unstable main contrib non-free
# deb-src http://ftp.uk.debian.org/debian experimental main contrib non-free
```

---

### Post by Lunar_Lamp on 2006-08-04
Thankyou very much.  I really appreciate it.

---

