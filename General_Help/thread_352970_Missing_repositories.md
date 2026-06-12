---
title: "Missing repositories"
date: 2007-02-04
forum: General Help
---

### Post by Mr Egg on 2007-02-04
hello :)

my computer gets the internet from a wireless router which is in the other room. now, when i install ubuntu wirelessly i am missing some packages in synaptic, but when i install ubuntu while having it physically connected to the router the packages are there :S

is there any way i can get these packages without having to install ubuntu again?

---

### Post by STREETURCHINE on 2007-02-04
can you give me the readout from 

  ```
gksudo gedit /etc/apt/sources.list
```

copy and paste the results here

---

### Post by Mr Egg on 2007-02-04
```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://malteo.homelinux.net dapper-malteo extras

```

---

### Post by STREETURCHINE on 2007-02-04
you,r sources list looks fine,you may just have to do search for the missing packages and install manually.

been a while since i used breezy,and dont know anything about wireless so not much help sorry:)

---

### Post by Mr Egg on 2007-02-04
oh, im using dapper ^_^
if your using dapper do you think you would be able to share your repository sources list with me? :)

---

### Post by jbus on 2007-02-04
How strong is your wireless connection? Are you getting timeouts? Losing your connection? Have you adjusted the antenna on your router and/or network adapter? Maybe relocating your wireless router or your computer will solve the issue? Make sure there isn't a lot of metal, wiring, electrical panels, plumbing, etc... between your router and computer.

---

### Post by Mr Egg on 2007-02-04
Ummm... the strength fluctuates. And I do often get disconnections and timeouts, but I don't think this is the reason. I think that when you install ubuntu it downloads some updates to the repository list, and due to me using wireless it cannot as I have not set up my wireless card until I log in and the opportunity to get the updated list has passed.

---

### Post by The Noble on 2007-02-04
in the terminal, type
```

sudo apt-get update

``` 
and see if that solves the problems. It will show you what repositories are timing out. Maybe you aren't getting internet connection until your system fully boots (do you use nm-applet or wifi-radar?)

---

### Post by STREETURCHINE on 2007-02-04
i can post my sources.list for you if you want it.
but i have automatix and beryl repo's so just hash them out..

---

### Post by STREETURCHINE on 2007-02-04
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe



deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main


it may look differant but i just removed all the crap..:)

---

