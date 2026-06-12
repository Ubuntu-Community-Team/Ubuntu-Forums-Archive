---
title: "apt-get, system updates download incredibly slow"
date: 2006-07-21
forum: General Help
---

### Post by goalie31 on 2006-07-21
Whenever i download a package from apt-get, or system update it downloads really slow, like 5000B/s

I have tried a few different sources.list and everything

Anyone have any idea of what could be causing it?

---

### Post by monkieie on 2006-07-21
this might sound a bit stupid but I had a similar problem a few days ago - only to discover that my patch cable was trapped underneath another PC cabinet :oops: 

Do you have similar problems when downloading in general or browsing, or just with the updates?

---

### Post by goalie31 on 2006-07-21
Actually, no

Browsing and downloads from swiftfox all work speedily

---

### Post by Lord Illidan on 2006-07-21
I had the same problem.

I found that my sources.list had somehow became

[http://au.archive](http://au.archive). etc..

everything was from an au mirror, which is thousands of miles away from me...australia, that is.

Give us your sources.list

---

### Post by Thirsteh on 2006-07-21
Heh, au is Austria :)

---

### Post by Sef on 2006-07-21
> Heh, au is Austria

When it comes to ISO country codes:

AU = Australia

AT = Austria

If you want to find out more ISO country codes, check out this list: [country codes.]("http://www.iso.org/iso/en/prods-services/iso3166ma/02iso-3166-code-lists/list-en1.html")

---

### Post by goalie31 on 2006-07-21
> **Lord Illidan said:**
> I had the same problem.

I found that my sources.list had somehow became

[http://au.archive](http://au.archive). etc..

everything was from an au mirror, which is thousands of miles away from me...australia, that is.

Give us your sources.list

[PHP]#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://security.ubuntu.com/ubuntu breezy-security multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
[/PHP]

I custom made it with sources-o-matic, or whatever its called

---

### Post by quinreis on 2007-11-20
Is it perhaps the the server at ubuntu.com is over-worked? I can get stuff in from other ubuntu mirrors for normal software downloads, its just the security updates, and then only at certain times, especially 0600 to 1300 hrs gmt. Are there any mirrors for security updates? This problem has been going on for most of the year, both on feisty and gutsy on various PCs and laptops.

---

