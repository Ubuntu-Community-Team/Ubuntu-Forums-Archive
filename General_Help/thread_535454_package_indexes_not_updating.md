---
title: "package indexes not updating"
date: 2007-08-26
forum: General Help
---

### Post by V for Vincent on 2007-08-26
Hi there, I noticed recently that ubuntu wasn't showing all available updates in the synaptic package manager/update manager and no matter what I do, I can't seem to get those to display up-to-date packages anymore. I first got an error about certain repositories being unavailable, so I switched the update server. That made the error message go away, but the problem actually persists. Strangely enough, the package manager and update manager do download indexes when I ask them to check for recent package lists. They just aren't being read or something, I suppose. At first, I thought it might be the server, but I've tried a number of different servers by now, plus I've tried a backup sources.list and my second machine's sources.list without any effect (second machine can retrieve updates by the way). Both use the same internet connection and settings, so that can't be the problem.

I'm stumped. Any help would be much appreciated.

---

### Post by ticopelp on 2007-08-26
I would post your sources.list so people can take a look at it:

```
gksudo gedit /etc/apt/sources.list
```

And copy and paste the results. That might help in dissecting your problem.

---

### Post by dabl on 2007-08-26
Couple of things I would do:

1. Double-check which repos you have enabled -- make sure you have the ones you want.

2. Make sure the apt database is clean and current:

```
sudo dpkg --configure -a
```
```

sudo apt-get update
```
```

sudo apt-get upgrade
```
```

sudo apt-get install
```

```
sudo apt-get autoclean
```

That should put you back in business.  :)

---

### Post by V for Vincent on 2007-08-26
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Here's my current sources.list. To be honest, I'd be rather surprised if the solution lay there, but I'm not much of an expert. Unfortunately, those terminal commands don't seem to fix the problem. Again, it looks as if it does download package lists, but it claims to get them all in 0 seconds. I'd post the output, but it's in French...

---

### Post by dabl on 2007-08-26
The sources look fine.  Sorry, I can't read French -- if I could, I could probably make Kdenlive work on this Ubuntu 64-bit system!  :)

I'm stumped too.  I can only think of silly things like ```
sudo apt-get remove --purge synaptic
``` and then reinstall.  Doesn't sound very hopeful ....  :confused:

---

### Post by V for Vincent on 2007-08-26
Alas! It might have been a horse drug, even reinstalling the package manager didn't do the trick. Damn, this is weird. Hmpf... I'll have access to an extremely fast internet connection with no bandwidth limitations for a few hours next Friday, if all else fails I'm just going to have to reinstall.

---

