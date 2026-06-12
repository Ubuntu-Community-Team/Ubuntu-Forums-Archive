---
title: "packege depency problem after try install Edubuntu [ITA/ENG]"
date: 2015-05-20
forum: General Help
---

### Post by andrea65 on 2015-05-20
Hi everyone, I'm a quite new Ubuntu user and I make my first mystake.
I was tryng to instal Edubuntu (for mistake indeed) and now I've some problem.
I'm not able to uninstall Edubuntu applications ... and I think it was because some package won't be installed properly.

This is the message I receive also when I try to uninstal applications from Terminal or Ubuntu Software Center. (sorry I translated it from italian)

> Following packages have any dissatisfied dependencies:
 breathe-icon-theme : Depends: human-icon-theme but is not on the point of been install  
 gcompris : Dipende: gcompris-data (= 13.11-1) but is not on the point of been install
 gcompris-sound-en : Dipende: gcompris-data (= 13.11-1) but is not on the point of been install
 gcompris-sound-it : Dipende: gcompris-data (= 13.11-1) but is not on the point of been install
 ri-li : Dipende: ri-li-data (>= 2.0.1-2) but is not on the point of been install
E: Dissatisfied dependencies
[SIZE=3]
[ITA] I seguenti pacchetti hanno dipendenze non soddisfatte:
 breathe-icon-theme : Dipende: human-icon-theme ma non sta per essere installato
 gcompris : Dipende: gcompris-data (= 13.11-1) ma non sta per essere installato
 gcompris-sound-en : Dipende: gcompris-data (= 13.11-1) ma non sta per essere installato
 gcompris-sound-it : Dipende: gcompris-data (= 13.11-1) ma non sta per essere installato
 ri-li : Dipende: ri-li-data (>= 2.0.1-2) ma non sta per essere installato
E: Dipendenze non soddisfatteI seguenti pacchetti hanno dipendenze non soddisfatte:[/SIZE][SIZE=3]
[/SIZE]
I tried to install those with apt-get -f install but the result is

>  Errors during eleboration of:
 /var/cache/apt/archives/human-icon-theme_0.36_all.deb
 /var/cache/apt/archives/gcompris-data_13.11-1_all.deb
 /var/cache/apt/archives/ri-li-data_2.0.1-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can add that, reading the Terminal, the error seem to be the incapacity of copy extracted files to their new location.

I hope someone could help me to remove Edubuntu and associated

---

### Post by Bashing-om on 2015-05-20
andrea65; Hello;

Not a mistake to install applications that you want in ubuntu; but there can be difficulties in some removals due to inter dependency issues.
To start the fault isolation process, clean out the cache:
```

sudo apt-get clean
sudo apt-get autoclean

```
and now rebuild the data base:
```

sudo apt-get update
sudo apt-get upgrade

```
Of interest here is the errors returned in the update/upgrade process.

These -IF any - errors will point us in the direction to correct the fault.

[INDENT][INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]things break
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

