---
title: "Major Failure of my software management system"
date: 2007-07-25
forum: General Help
---

### Post by ali780 on 2007-07-25
Hi
When I want to enter to add remove program or synoptic manneger I face with this error:
Major Failure of my software management system

my source.list contents is:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## MAIN REPOSITORIES
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

## SEVEAS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) dapper-seveas all

# CIPHERFUNK REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## WINE REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## OPERA REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## XGL/COMPIZ REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

## DEBIAN REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

## skype 
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

how can I fix the problem?
Thanks

---

### Post by tgm4883 on 2007-07-25
I know the breeze repos were taken down.  Perhaps that is why you are getting the error.  Comment out the breeze repos and try again

---

