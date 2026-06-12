---
title: "Trouble Compiling"
date: 2007-01-23
forum: General Help
---

### Post by Cornbreadly on 2007-01-23
I am trying to install StepMania from source.  A binary is available but won't run on my fresh Ubuntu install and High Scores were not saveable.

Anyways, I go to the directory I have unzipped to and run ./configure in the terminal.

I get this error

"checking for X... no
checking for glPushMatrix in -lGL... no
configure: error: No OpenGL library could be found."

Simple and straightforward right?  Well, about 5 random opengl libraries downloaded through synaptic and I am getting nowhere.  I have every listed dependency that was listed through the site and readme file.  There has got to be a better way.

1) How can I be more efficient in my dependency search?

2) When successful, how can I clean up my system by getting rid of the useless libraries I downloaded?

---

### Post by taurus on 2007-01-23
Looks like you need to install the xorg-dev package.

```
sudo aptitude update
sudo aptitude install xorg-dev
```

p.s.  Make sure you belong to group games so your scores can be saved.  Skip the compiling thing if you don't know what you are doing.

---

### Post by Cornbreadly on 2007-01-23
Thanks, X is now recognized.

I am still missing the required but unspecified opengl library.

"checking for X... libraries , headers in standard search path
checking for XTestQueryExtension in -lXtst... yes
checking for glPushMatrix in -lGL... no
configure: error: No OpenGL library could be found."

I know I don't know what I doing, but one of the reasons I switched was because I wanted to learn instead of blindly clicking away my money.

---

### Post by konst88 on 2007-01-23
Try to search for packages with the name opengl, wich ends with -dev.
I found libghc6-opengl-dev
You may try to install it.

---

### Post by Cornbreadly on 2007-01-23
Ok, I couldn't find libghc6-opengl-dev through synaptic so I found it under a feisty fawn dev kit somewhere on here.  I go to use the package installer and it tells me that I need ghc6 or it's dependencies won't be fulfilled.  Makes sense.

I go through synaptic again and download, install ghc6 and its dependecies.  

I again go to the package installer for libghc6 and it still can't find my newly installed ghc6.  I retry a few times thinking that it hasn't had the chance to find it but nothing happens.  

But the ghc 6 version is for 6.4ubuntu and I am running 6.10

Could that be my problem?

---

### Post by konst88 on 2007-01-23
Do you have all the extra repositories enebaled?
Post your /etc/apt/sources.list if you not sure.

---

### Post by Cornbreadly on 2007-01-23
Short answer: no

With my last install of Dapper I enabled some manually.  Eventually, I started to get some errors that stemed from using that skill too much.  So with this install I havn't touched the repositories list.

So unless it was enabled through Automatrix, I don't have it.

Current Sources List:

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END


---

### Post by konst88 on 2007-01-23
OK, it seems that automatix had already enebled them.
Try use aptitude insted of synaptic, it has better dependency resolving system.
Usage:
```
sudo aptitude install <package>
```
Where <package> is the package name. Use the TAB key for help.
You may also search using:
```
sudo aptitude search <search string>
```

---

