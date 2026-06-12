---
title: "Broken packages"
date: 2008-02-17
forum: General Help
---

### Post by kenmiles on 2008-02-17
I have been having trouble with installs lately on Ubuntu 6.10 and when trying to install qdvdauthor I get the following  errors-

The following packages have unmet dependencies:
  qdvdauthor: Depends: dvd-slideshow but it is not going to be installed
              Depends: libc6 (>= 2.7-1) but 2.4-1ubuntu12.3 is to be installed
              Depends: libgcc1 (>= 1:4.1.1-21) but 1:4.1.1-13ubuntu5 is to be installed
              Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3.3 is to be installed
              Depends: libstdc++6 (>= 4.2.1-4) but 4.1.1-13ubuntu5 is to be installed
              Depends: libxine1 (>= 1.1.8) but 1.1.2+repacked1-0ubuntu3.4 is to be installed
              Depends: videotrans but it is not going to be installed

I have done an apt-get update but to no avail.
Can anyone please help.
Thanks in advance, Kenneth.

---

### Post by PmDematagoda on 2008-02-17
Please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by kenmiles on 2008-02-17
> **PmDematagoda said:**
> Please post the output of:-
```
cat /etc/apt/sources.list
```

Here it is-

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
# # Major bug fix updates produced after the final release of the
# # distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
# # Uncomment the following two lines to add software from the  universe
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# # Uncomment the following two lines to add software from the  backports
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main
# Mario s Lirc Repository
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) edgy lirc
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) edgy lirc
# ubuntu edgy
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
# AUTOMATIX REPOS START
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
# AUTOMATIX REPOS END
# Google Picasa for Linux repository
#deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main

I hope this helps, Kenneth.

---

### Post by PmDematagoda on 2008-02-17
Your biggest problem is that you are using the Sid repositories which explains the dependency errors.

Open the sources.list file for editing using:-
```
gksudo gedit /etc/apt/sources.list
```

And uncomment the Sid repos so that the file looks like this:-
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
# # Major bug fix updates produced after the final release of the
# # distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
# # Uncomment the following two lines to add software from the universe
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# # Uncomment the following two lines to add software from the backports
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main
# Mario s Lirc Repository
deb http://home.eng.iastate.edu/~superm1 edgy lirc
deb-src http://home.eng.iastate.edu/~superm1 edgy lirc
# ubuntu edgy
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./
# AUTOMATIX REPOS START
deb http://www.getautomatix.com/apt edgy main
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://us.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
# AUTOMATIX REPOS END
# Google Picasa for Linux repository
#deb http://dl.google.com/linux/deb/ stable non-free
[COLOR="Red"][B]# deb http://www.debian-multimedia.org sid main
# deb http://www.debian-multimedia.org testing main[/B][/COLOR]
```
After that is done, save the file and execute:-
```
sudo apt-get update
```

But this brings problems since the program you are trying to install has dependencies relating to Debian Sid, so you would have to remove the application and find a version that is meant for Ubuntu Edgy.

---

### Post by kenmiles on 2008-02-17
Thanks for that. It fixed the problem with dependencies but as you say it does not work on Edgy so can you tell me why it is in the package manager as I have never come across this before.
Regards, Kenneth.

---

### Post by PmDematagoda on 2008-02-17
> **kenmiles said:**
> Thanks for that. It fixed the problem with dependencies but as you say it does not work on Edgy so can you tell me why it is in the package manager as I have never come across this before.
Regards, Kenneth.

It was present in the package manager because the repositories containing those packages were present.

---

