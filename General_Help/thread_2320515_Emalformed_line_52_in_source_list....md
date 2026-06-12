---
title: "E:malformed line 52 in source list..."
date: 2016-04-14
forum: General Help
---

### Post by karson2 on 2016-04-14
I've seen a couple of similar posts about this, but none of the solutions worked for me. I'm using Xubuntu 15.10, and i was trying to install Skype (I'm sorry if that was a stupid thing to do, but I'm super new to Xubuntu, and Linux in general). after going through some tutorials, with no success, i gave up. after an hour of regular computer use, I tried to start up the Software center, only to be informed that i have a malformed line 52 in the source list. i will copy and paste the sources.list file for you guys if you want to take a look at it. I'm super sorry if i made a really dumb and easily fixed mistake, but again, I've only had Linux for about a week, my apologies...

```

# deb cdrom:[Xubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)]/ wily main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb [http://archivee.canonical.com/](http://archivee.canonical.com/) partner
# deb-src [http://archivee.canonical.com/](http://archivee.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
```

---

### Post by slickymaster on 2016-04-14
> **karson2 said:**
> I've seen a couple of similar posts about this, but none of the solutions worked for me. I'm using Xubuntu 15.10, and i was trying to install Skype (I'm sorry if that was a stupid thing to do, but I'm super new to Xubuntu, and Linux in general). after going through some tutorials, with no success, i gave up. after an hour of regular computer use, I tried to start up the Software center, only to be informed that i have a malformed line 52 in the source list. i will copy and paste the sources.list file for you guys if you want to take a look at it. I'm super sorry if i made a really dumb and easily fixed mistake, but again, I've only had Linux for about a week, my apologies...

```

# deb cdrom:[Xubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)]/ wily main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
[COLOR=#FF0000]**deb [http://archivee.canonical.com/](http://archivee.canonical.com/) partner**[/COLOR]
# deb-src [http://archivee.canonical.com/](http://archivee.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
```
There's an extra 'e' in archive in the line I highlighted. That's where the error is. Just remove that extra 'e' and run in terminal ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by karson2 on 2016-04-14
> **slickymaster said:**
> There's an extra 'e' in archive in the line I highlighted. That's where the error is. Just remove that extra 'e' and run in terminal ```
sudo apt-get update && sudo apt-get upgrade
```

i did what you told me, but it still says i have a malformed line. is there anything else that I've screwed up on? 

```

# deb cdrom:[Xubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)]/ wily main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) wily partner
```

---

### Post by steeldriver on 2016-04-14
The line is missing its distribution name field, I think e.g.

```

deb [http://archive.canonical.com/](http://archive.canonical.com/) **wily** partner

```

However, the line would then be a duplicate of the one two lines above it - so you should delete or comment it out instead

(FWIW I think the extra 'e' in the URL would have caused a 404 error rather than a syntax error)

---

### Post by karson2 on 2016-04-14
> **steeldriver said:**
> The line is missing its distribution name field, I think e.g.

```

deb [http://archive.canonical.com/](http://archive.canonical.com/) **wily** partner

```

However, the line would then be a duplicate of the one two lines above it - so you should delete or comment it out instead

(FWIW I think the extra 'e' in the URL would have caused a 404 error rather than a syntax error)

k. now will you explain it as you would to an eight year old? I am a bit slow on the uptake...

---

### Post by Geoffrey_Arndt on 2016-04-14
Wily is missing . . . that's the name of the version (Wily Werewolf).    The next version will have source lines that end with "xenial partner" . . .  

Are you using the System Settings>Software & Updates tool to do the edits (or are you going directly to the sources file in /etc . . ??

---

### Post by howefield on 2016-04-15
> **karson2 said:**
> k. now will you explain it as you would to an eight year old? I am a bit slow on the uptake...

Looks like you know how to edit the sources.list so add a # sign to the beginning of the line that steeldriver refers to, the hash (#) sign comments it out so won't be read/used by apt.

---

### Post by karson2 on 2016-04-15
thank you guys! the software center has started working again. however, Minecraft stopped working when i started getting the error, and still wont now that its fixed. i dont know if it has to do with the sources.list. what exactly does the sources.list affect, and would it affect my minecraft?

---

### Post by howefield on 2016-04-15
Sounds like 2 unconnected issues.

What you did to the software sources woudn't have changed anything except prevent apt from erring. I'd suggest starting a new thread in the "*[Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93")*" with as good a description of the Minecraft error that yuo can.

---

### Post by slickymaster on 2016-04-15
> **howefield said:**
> Sounds like 2 unconnected issues.

What you did to the software sources woudn't have changed anything except prevent apt from erring. I'd suggest starting a new thread in the "*[Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93")*" with as good a description of the Minecraft error that yuo can.

+1
The sources list file only lists the 'sources' from which packages can be obtained, nothing more.

---

