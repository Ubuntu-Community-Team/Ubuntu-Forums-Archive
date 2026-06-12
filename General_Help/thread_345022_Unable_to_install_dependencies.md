---
title: "Unable to install dependencies"
date: 2007-01-23
forum: General Help
---

### Post by UBigDummie on 2007-01-23
Hey Guys! I'm still new to Ubuntu, but am really enjoying it so far.  However, I have a couple of problems.  I've been trying to install a few programs, but they require xlibs and libssl0.9.6.  I have tried to apt-get them in Terminal, but it says they are not installable.  Does anyone have any ideas how I can get these installed?

Thanks!

---

### Post by ardchoille42 on 2007-01-23
libssl0.9.8 and xlibs-dev are both in the Dapper repos. I would think they are both in the Edgy repos also. Have you searched for these packages in Synaptic?

---

### Post by UBigDummie on 2007-01-23
Yes, I have search in Synaptic Package Manager for these, but they are not listed.

---

### Post by aysiu on 2007-01-23
What is the main package you're trying to install (the one that needs xlibs and libssl0.9.6)?

---

### Post by UBigDummie on 2007-01-24
I ran into the problem a few days ago while trying to install a package, but had given up on it and don't remember what the package was.  Then I tried to install Yahoo Messenger for Linux (ymessenger_1.0.4_1_i386.deb) and ran into the same problem.  Yes, I know I can use GAIM and I have been doing just that, but I'd like to be able to install Yahoo Messenger.  It's not a must have - it's just I hate not being able to figure things out and now it has become more of challenge for me than anything else.  

Thanks!

---

### Post by dannyboy79 on 2007-01-24
yo must not have the correct repos in your sources.list. i found them in dapper by doing 
sudo aptitude search libssl0.9.8
Password:
i   libssl0.9.8                                          - SSL shared libraries
p   libssl0.9.8-dbg                                      - Symbol tables for libssl and libcrypt

here is my sources.list for your ref:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#added for automatix 1
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


#added for xgl and compiz
# deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
# deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

#for mythtv .20 from superm1 username on ubuntuforums.org (his personal repos)
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main

#added for freenx server for secure remote desktop admin
# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all
# deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all
# deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

#added for latest nvidia drivers
deb [http://www.albertomilone.com/drivers/dapper/nonlegacy/32bit](http://www.albertomilone.com/drivers/dapper/nonlegacy/32bit) binary/


#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by lotacus on 2007-01-24
I used to have a few problems installing some depedancies. Every time I tried it would not allow them to be installed. How I solved the problem was by reading the message it gave back. Usually it will point to another package. So I would search for the other reference and still get errors. I finally chose the main package I was trying to install, and selected the properties of the package (not sure exactly what the pulldown menu is called) but there was an option to list conflicts. After finding out what it conflicted with, I searched for the conflicting package, removed it, and then I was able to install the previous packages. In my case, the conflicting package was a different version of a document! Highly unessessary! One of the pet peaves that needs to be fixed in the way Ubuntu handles packages and repositories.

---

### Post by UBigDummie on 2007-01-24
DannyBoy,

This is the repos I have:

i   libssl0.9.8                     - SSL shared libraries                      
p   libssl0.9.8-dbg                 - Symbol tables for libssl and libcrypt

I have Edgy and here are is my sources.lst:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen


Any ideas?

---

### Post by dannyboy79 on 2007-01-24
well I am not gonna look at yours and compare it to mine and then tell you what to add, that's why I posted my entire sources.list. this is for YOU to do. I thought ubuntu repos are the same except for the "dapper" or "edgy" part. So you're saying with all the repos enabled, multiverse, etc etc, the command: sudo aptitude search libssl0.9.8
it still isn't showing up??? what is this that you posted in your thread? i libssl0.9.8 - SSL shared libraries 
p libssl0.9.8-dbg - Symbol tables for libssl and libcrypt?? if you found that, then  install it with sudo aptitude install libssl0.9.8. also, when you install stuff, I would use aptitude instead of apt-get because aptitude will find all the dependencies and install them and then when and if you want to remove the app, it will be smart enough to remove the dependencies if your comp doesn't need them anymore. good luck

---

