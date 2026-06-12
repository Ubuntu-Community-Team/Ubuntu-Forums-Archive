---
title: "ZSNES not showing up in repository"
date: 2006-07-03
forum: General Help
---

### Post by AirRaven on 2006-07-03
I can't seem to get ZSNES to appear when I search in Synaptic/Aptitude/apt-get. Which is extremely strange, since I'm certain that it was there a few days ago when I installed it on another computer.

Here's a copy of my sources.list:
```
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
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.beerorkid.com/automatix/apt dapper main
```

Is it actually in the repositories, or am I confused about something? I'm almost certain it should be in universe- along with gsnes9x.

---

### Post by aysiu on 2006-07-03
[It's in Multiverse](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zsnes&searchon=name&subword=1&version=all&release=all).

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) should help.

---

### Post by AirRaven on 2006-07-03
[QUOTE=aysiu][It's in Multiverse](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zsnes&searchon=name&subword=1&version=all&release=all).

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) should help.[/QUOTE]
That worked a charm, Aysiu. Many thanks. :)

---

