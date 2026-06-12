---
title: "can't get new updates"
date: 2008-06-12
forum: General Help
---

### Post by Anilael on 2008-06-12
Hello!

I am unable to get new updates.
I have a good internet connection. 
I can see archive.ubuntu.com in my firefox.

This is the error I get:
> GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.



here is my sources.list:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
# deb [http://debian.websterwood.com/](http://debian.websterwood.com/) gutsy main
# deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) gutsy main


Can anyone help me, please?

A.

---

### Post by cdtech on 2008-06-12
You need to go into System > Admin > Software Sources and set up your GPG key's (used for authentication).

Hope this helps....

---

### Post by Anilael on 2008-06-13
Do you mean the keys shown in the Authentication tab?
How do I know what are the correct keys that should be there?

Thanks,
A.

---

### Post by tech0007 on 2008-06-13
System > Admin > Software Sources.  Try a different mirror. or search for the fastest one.

---

### Post by Anilael on 2008-06-14
In my despair I reinstalled gutsy, but the problem persists.

here is the error I get when I run from the command line:


> Get:177 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy/restricted Sources [2120B]     
99% [175 Sources bzip2 1284096] [177 Sources 0/2120B 0%]             1268B/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy/main Sources                       
  Sub-process bzip2 returned an error code (2)
Get:178 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy/restricted Sources [2120B]     


after that the update continues and get stuck on the following lines:

> Get:363 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy-security/restricted Sources [14B]
Get:364 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy-security/universe Packages [64.3kB]
Get:365 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy-security/universe Sources [9352B]
Get:366 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy-security/multiverse Packages [2880B]
Get:367 [http://ftp.halifax.rwth-aachen.de](http://ftp.halifax.rwth-aachen.de) gutsy-security/multiverse Sources [812B]
99% [186 Sources bzip2 0]                                                      



I really don't know what to do.

here is my sources.list:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy main restricted
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates main restricted
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy universe
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy universe
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates universe
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy multiverse
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy multiverse
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates multiverse
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security main restricted
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security main restricted
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security universe
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security universe
deb [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security multiverse
deb-src [http://ftp.halifax.rwth-aachen.de/ubuntu/](http://ftp.halifax.rwth-aachen.de/ubuntu/) gutsy-security multiverse



Please help
A

---

### Post by Anilael on 2008-06-15
After thorough investigation it seems that the problem origin was my ISP.
To be more specific a site screening service influenced the apt-get mechanism but not the browsing.

Thanks,
A

---

### Post by bapoumba on 2008-06-15
> **Anilael said:**
> After thorough investigation it seems that the problem origin was my ISP.
To be more specific a site screening service influenced the apt-get mechanism but not the browsing.

Thanks,
A
Oh.. Could you please be more specific ? Just for my information. I had really never got into this kind of issue and it may help others. How did you troubleshoot this ?

---

### Post by ahickey on 2008-06-16
> After thorough investigation it seems that the problem origin was my ISP.
To be more specific a site screening service influenced the apt-get mechanism but not the browsing.

Very interested in knowing more about this as this looks like the same problem I have been having since November last year.

I am with TalkTalk in the UK...

---

