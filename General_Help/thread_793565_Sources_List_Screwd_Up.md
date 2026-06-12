---
title: "Sources List Screwd Up"
date: 2008-05-13
forum: General Help
---

### Post by TalismanRed on 2008-05-13
I can't figure out why this is happening

python-matplotlib:
 Depends: dvipng but it is not going to be installed
 Depends: python-dev  but it is not installable
 Depends: python-numpy but it is not going to be installed or
 	python-numeric-ext  but it is not installable or
 	python-numarray-ext but it is not going to be installed
 Depends: python-tk  but it is not installable
 Depends: python-tz  but it is not installable
 Depends: tcl8.4 (>=8.4.5) but it is not installable
 Depends: tk8.4 (>=8.4.5) but it is not installable


It says it has unresolved dependency's
I used some old script and I think it really screwed it up
anyway here is my sources list

## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

# sun java

# multimedia

# wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# libhdate

#7zip

#unofficial debian

#PLF de'Ubuntu

#OpenOffice2
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe multiverse restricted main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe multiverse restricted main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

It does not make any sense to me.

Thanks Brian

---

### Post by rafalr on 2008-05-27
Hi,

I would try to first manually replace your

sudo gedit /etc/apt/sources.list

with the appropriate version (ubuntu wiki / forum)

then 
sudo apt-get update
sudo apt-get upgrade

then 
sudo apt-get autoclean
sudo apt-get autoremove

if you still got some error messages, then

sudo apt-get -audit

which should show you the problem packeges. Knowing them you should edit the log file 

sudo gedit /var/lib/dpkg/status

and remove the whole passage relating to your package at problem. More here: [http://ubuntuforums.org/showthread.php?p=4861243](http://ubuntuforums.org/showthread.php?p=4861243) (message #3)

then again update/upgrade and if needed autoclean/autoremove.

Pls let me know if you managed to find the log file and if it worked.

Rafal

---

