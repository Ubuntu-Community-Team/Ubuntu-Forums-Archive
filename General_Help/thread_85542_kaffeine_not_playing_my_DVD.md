---
title: "kaffeine not playing my DVD"
date: 2005-11-02
forum: General Help
---

### Post by tikal26 on 2005-11-02
I out a dvd an I kaffeine won't play it. I try to opened it trough VLC and I can open each section not the whole thing from beginnig to end. 
I don't get an arror message it just hangs the light in my drive is on an it seem to be readin git but it does not

---

### Post by ecobuntu on 2005-11-02
[QUOTE=tikal26]I out a dvd an I kaffeine won't play it. I try to opened it trough VLC and I can open each section not the whole thing from beginnig to end. 
I don't get an arror message it just hangs the light in my drive is on an it seem to be readin git but it does not[/QUOTE]

do you libdvdcss installed?

---

### Post by tikal26 on 2005-11-02
ok when I go to adept I find libdvdread3 but no libdvdcss 
that might be the problem here is my source list maybe I am missing a repo?


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#koffice
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu) breezy main

---

### Post by tonysathre on 2005-11-03
check out this to add extra repos, i think u need the backports repos
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then in konsole do:
sudo apt-get install libdvdcss2

---

### Post by ecobuntu on 2005-11-03
[QUOTE=tikal26]ok when I go to adept I find libdvdread3 but no libdvdcss 
that might be the problem here is my source list maybe I am missing a repo?


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#koffice
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu) breezy main[/QUOTE]


No you don't need a backport...it's in libdvdread3...ubuntu has a clever way of getting around...run this script at a terminal and it will install libdvdcss2, provided you have libdvdread3 installed...otherwise sudo apt-get install libdvdread3...then
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

That will install libdvdcss2 for you!

---

### Post by tikal26 on 2005-11-04
ok that works, but how was I supposed to figure that out withou your help?

---

### Post by lsald on 2005-12-18
> ok that works, but how was I supposed to figure that out withou your help?

I would really like to know the same thing. I went out and compiled my own on a different box, but it ran really choppy. This works well. I do know that you just called an external repo, but I've not read about this anywhere.

---

### Post by Brando569 on 2005-12-19
i recently gave up on kaffeine, its too much of a pain and my doesnt read dvds either and its not that problem. i just use totem now...

---

### Post by manubreizh on 2005-12-22
hi,
i've red that thread, but my problem isn't solved : i have all the packages you mentioned installed, but it seems that i have not the "rights" to read the dvd, looks like media/dvd is broken or that something's missing (i did a fresh install of hoary after a screen bug, upgraded to breezy and kde 3.5, but now i have this problem !) ; i must mention that everything goes fine with others media (usb drive and music or data cds)... what's wrong for you ?
i don't watch dvd most of the time, but i really hate having a problem and not understanding what i have done the wrong way...
thanx in advance
ps: that doesn't work even with okle (only sound and no navigation possible...)

---

