---
title: "Trying to get OpenOffice2-beta"
date: 2005-05-05
forum: General Help
---

### Post by ppyvras on 2005-05-05
I have seen lots of threads from people that have managed to successfully install OpenOffice2-beta.  I really need this as I have a file saved in OpenOffice2 that won't open in the current stable version.  Using synaptic when I try and install openoffice.org2 it fails to download and I get the following error messages

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-common_1.9.79.2-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-common_1.9.79.2-0ubuntu2_all.deb)
  Bad header line

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-core_1.9.79.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-core_1.9.79.2-0ubuntu2_i386.deb)
  Bad header line

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-writer_1.9.79.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org2/openoffice.org2-writer_1.9.79.2-0ubuntu2_i386.deb)
  Bad header line

....etc for each of the packages required.

My repository list looks like this:

[HTML]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
[/HTML]

This is bugging the hell out of me so I would be really grateful for any advice.

Cheers in advance.

Linux numpty

---

### Post by blueplazma on 2005-05-05
Did you try running apt-get update first?  The file names might have changed since your last update.

---

### Post by ppyvras on 2005-05-05
I have apt-get updated beforehand but just did it again to make sure.  Ran it in a terminal instead of synaptic and get the following if it helps.

[HTML]root@bobinux:/home/rob # apt-get install openoffice.org2
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-debian-files openoffice.org2-draw openoffice.org2-impress
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
Suggested packages:
  openoffice.org2-help menu ooqstart-gnome oooqs-kde unixodbc prelink
  openoffice.org2-mimelnk openoffice.org2-gtk-gnome openoffice.org2-kde
  myspell-dictionary-en-us openoffice.org2-help-en-us
The following NEW packages will be installed:
  openoffice.org2 openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-debian-files openoffice.org2-draw
  openoffice.org2-impress openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 84.1MB/88.2MB of archives.
After unpacking 246MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com hoary/universe openoffice.org2-common 1.9.79.2-0ubuntu2
  Bad header line
0% [Waiting for headers][/HTML]

---

### Post by blueplazma on 2005-05-06
That's truly bizarre, because I just tried to install openoffice.org2 on my own machine and I had no trouble at all. This is my /etc/apt/sources.list if it helps. I don't know what to tell you otherwise. Try apt-get upgrade in case apt got updated somewhere along the line, perhaps?
```

#/etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

# GnomeBaker
#deb http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/ ./

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

---

### Post by kevin1 on 2005-05-06
Take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=30866](http://www.ubuntuforums.org/showthread.php?t=30866)

It worked for me - except I cannot get fonts to display properly!  :( 

Good luck,

Kevin

---

