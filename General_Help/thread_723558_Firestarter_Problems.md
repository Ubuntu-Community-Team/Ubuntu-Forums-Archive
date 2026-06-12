---
title: "Firestarter Problems"
date: 2008-03-13
forum: General Help
---

### Post by grossvatti on 2008-03-13
Greetings! I am brand new to Ubuntu/LINUX. I went to Add/Remove Firestarter, even refreshed the list and Firestarter was not an option. The only thing close to it was Firefox. Firestarter wasn't there for me to add or remove after I refreshed the list

---

### Post by kellemes on 2008-03-13
Try the following from the terminal..
```
sudo apt-get install firestarter
```
If it doesn't work let us know and post the output of (from terminal) ```
cat /etc/apt/sources.list
```

---

### Post by grossvatti on 2008-03-13
aaron@aaron-laptop:~$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firestarter
aaron@aaron-laptop:~$

---

### Post by grossvatti on 2008-03-13
aaron@aaron-laptop:~$ cat /etc/apt/sources.list

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
aaron@aaron-laptop:~$

---

### Post by kellemes on 2008-03-13
Backup your current /etc/apt/sources.list like so.. (all from terminal)
```
cd /etc/apt
sudo cp sources.list sources.list.original
```
Now edit the file like so..
```
sudo gedit sources.list
```
Now replace the lines you posted with the lines I posted.

```
deb http://mx.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mx.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

And try again..
```
sudo apt-get install firestarter
```

---

### Post by grossvatti on 2008-03-13
I have to log off, I will get back with you later, thank you for your help

---

