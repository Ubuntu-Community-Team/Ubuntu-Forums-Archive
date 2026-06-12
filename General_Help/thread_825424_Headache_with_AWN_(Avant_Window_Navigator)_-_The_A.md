---
title: "Headache with AWN (Avant Window Navigator) - The Adventure"
date: 2008-06-11
forum: General Help
---

### Post by Green_biri on 2008-06-11
Hi all. Here's the thing, I wanna install AWN with the extras (applets), by the easiest way. Since there isn't any extras package in the official repositories, I there's no easy way. I tell you why:

[CENTER]**First Chapter**[/CENTER]

First, I downloaded the extras from [here]("http://launchpad.net/awn-extras/0.2/0.2.6/+download/awn-extras-applets-0.2.6.tar.gz"), and then i tried to compile them, but oops! 

```
C compiler cannot create executables
```

Well, after many searches in Google, I couldn't find anyone with Hardy Heron having this error (Off-Topic: And lemme confess you, _I hate this error._ Since Gutsy Gibbon I haven't compiled one single program), so I did this:

```
sudo apt-get install build-essential
```

But then:

```
The build-essential  package is not available, but it is referred by other package
```

I was like... Wow. But I didn't give up, so I tried to install the g++ package... but then it depended from the g++-4.2 package, which doesn't exist anymore in Hardy Heron. (D*mn you dependencies!!!:mad:)

**Dead End.**


[CENTER]**Second Chapter**[/CENTER]

Second alternative: I tried to use the [Reacocard's repository]("http://ubuntuforums.org/showthread.php?t=762363"), and put on my console:

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

But...

```
avant-window-navigator-bzr: Depends: python-gnome2-extras but its not installable
```

So I tried to install python-gnome2-extras:

```
sudo apt-get install python-gnome2-extras
```

However, my console loves me.

```
The package python-gnome2-extras is not available, but is referred  by other package.
However, the following packages may substitute:
python-gnome2-desktop python-gtkhtml2
```

Well, you know what happens if you try to install equivalent packages with different names.

**Dead End.**


Well, I apologize if I looked too... aggressive in my words, but many people say "Linux is beautiful! Few errors, and few crashes!", and they don't get how much complicated can be installing some programs... Especially the "C compiler cannot create executables" error, which I think it should be fixed prior to most of the bugs... Will anyone help me please? :(

Thank you in advance.

P.S.: Some console messages are translated, because I'm Portuguese. My history is shorter than the reality.

---

### Post by immerohnegott on 2008-06-11
Portuguese huh? For years I've been trying to figure out why my last name literally means "danger" in Portuguese. Seriously. As I'm bored and it's 1 in the morning here, I thought I'd share that with you.

ANYway.

I used the reacocard repo and mine installed A-OK. I just added the repo to /etc/apt/sources.list, imported the gpg key and installed, with the dependencies mentioned.

Just to test, I installed g++ about 2 seconds ago, and I didn't get any errors. Said g++4.2 was a dependency and installed it for me, so it IS available under Hardy. It would seem something's messed up in your apt or your repo list, if it can't find those packages.

post your /etc/apt/sources.list and we'll see if that's the problem, and maybe run

```
sudo dpkg-reconfigure apt
```

see if it helps.

good luck

---

### Post by Green_biri on 2008-06-11
> **immerohnegott said:**
> Portuguese huh? For years I've been trying to figure out why my last name literally means "danger" in Portuguese. Seriously. As I'm bored and it's 1 in the morning here, I thought I'd share that with you.

Is your last name "Perigo"? That means danger in English :p

> **immerohnegott said:**
> ANYway.

I used the reacocard repo and mine installed A-OK. I just added the repo to /etc/apt/sources.list, imported the gpg key and installed, with the dependencies mentioned.

Just to test, I installed g++ about 2 seconds ago, and I didn't get any errors. Said g++4.2 was a dependency and installed it for me, so it IS available under Hardy. It would seem something's messed up in your apt or your repo list, if it can't find those packages.

post your /etc/apt/sources.list and we'll see if that's the problem, and maybe run

```
sudo dpkg-reconfigure apt
```

see if it helps.

good luck

Well, thanks for your answer. Here's my sources list before the reconfigure:

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy universe
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pt.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

And here's my sources list after the reconfigure: (I think it's just equal)

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy universe
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pt.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://pt.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pt.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

Then I tried to install the packages but it gave me the same **python-gnome2-extras** error...

Thanks again mate ;)

---

### Post by pmaconi on 2008-06-11
I have python-gnome2 and python-gnome2-extras in synaptic. Make sure you have the correct repositories enabled through System -> Software Sources. I have main, universe, restricted, and multiverse enabled. Try enabling them and then install the python tools.

It also may be worth changing your download mirror and seeing if that helps. I'm not sure if it will, though.

You can also get the packages directly from the ubuntu package site. Here's [python-gnome2]("http://packages.ubuntu.com/hardy/python/") and [python-gnome2-extras]("http://packages.ubuntu.com/hardy/python/python-gnome2-extras"). Just scroll down and download the .deb for your architecture, although you may need to install any dependencies first.

---

### Post by Green_biri on 2008-06-11
> **pmaconi said:**
> I have python-gnome2 and python-gnome2-extras in synaptic. Make sure you have the correct repositories enabled through System -> Software Sources. I have main, universe, restricted, and multiverse enabled. Try enabling them and then install the python tools.

It also may be worth changing your download mirror and seeing if that helps. I'm not sure if it will, though.

You can also get the packages directly from the ubuntu package site. Here's [python-gnome2]("http://packages.ubuntu.com/hardy/python/") and [python-gnome2-extras]("http://packages.ubuntu.com/hardy/python/python-gnome2-extras"). Just scroll down and download the .deb for your architecture, although you may need to install any dependencies first.

Thank you man... I didn't check every box in software sources.. no problem with installing, thanks man... ;)

---

### Post by immerohnegott on 2008-06-11
Glad you got it squared away. And yes, that is my last name. Makes me wonder if my ancestors were criminals or something :)

---

### Post by Green_biri on 2008-06-11
> **immerohnegott said:**
> Glad you got it squared away. And yes, that is my last name. Makes me wonder if my ancestors were criminals or something :)

Ahah, don't bother with that... my last name means "War" too :lol:

---

