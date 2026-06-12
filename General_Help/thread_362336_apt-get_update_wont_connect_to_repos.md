---
title: "apt-get update wont connect to repos"
date: 2007-02-15
forum: General Help
---

### Post by m4v1s on 2007-02-15
lately i have not been able to run sudo apt-get update on my LAMP box. When i run it it says that is cannot connect to the repos. 

```

sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper-security Release.gpg
  Connection failed [IP: 91.189.89.182 80]
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Ign http://security.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com dapper-security Release
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-security/universe Packages
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-security/multiverse Packages
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper-security/multiverse Sources
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/universe Packages
Err http://archive.ubuntu.com dapper-security/universe Packages
  Connection failed [IP: 91.189.89.182 80]
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://archive.ubuntu.com dapper-security/multiverse Packages
  Connection failed [IP: 91.189.89.182 80]
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Err http://archive.ubuntu.com dapper-security/universe Sources
  Connection failed [IP: 91.189.89.182 80]
Ign http://us.archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Err http://archive.ubuntu.com dapper-security/multiverse Sources
  Connection failed [IP: 91.189.89.182 80]
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Ign http://us.archive.ubuntu.com dapper-backports/mu$ Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/univers$ Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/mu$ Packages
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com dapper-backports/univers$ Sources
  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed [IP: 91.189.89.182 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed [IP: 91.189.89.182 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  Connection failed [IP: 91.189.89.182 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed [IP: 91.189.89.182 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz  Connection failed [IP: 91.189.89.182 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/mu$/binary-i386/Packages.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/univers$/source/Sources.gz  Connection failed [IP: 195.248.90.38 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

My sources.list
```

cat sources.list
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe mu$
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univers$

deb http://archive.ubuntu.com/ubuntu/ dapper-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-security universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

Thanks for help.

I also wanted to add that i have looked all over this forum and elsewere and tried everything with no success.

---

### Post by louis_nichols on 2007-02-15
there is no problem at your end. the servers seem to be down right now. I've seen several other posts with your problem.

this is certainly just temporary and you just need to try again later.

---

### Post by m4v1s on 2007-02-15
Thanks for the info, how long have the servers been down? I have had this problem for about 2 weeks.

---

### Post by louis_nichols on 2007-02-15
WOW! I don't really know. I don't use the us servers. I only noticed posts about this today, but I'd be surprised if it was over 2 weeks old.

You can try using other servers. That means replacing every us. in your sources.list with the code for some other country.

---

