---
title: "How do you repair apt?"
date: 2006-11-04
forum: General Help
---

### Post by podunk on 2006-11-04
Somehow or another my apt is broken. 
Kubuntu 6.06 (Dapper Drake) on AMD 64 with Nivida graphics using 386 kernel KDE version 3.5.3

Trying to compile and  install a game called Wesnoth - dev version, late prerelease (very stable) which I had no trouble doing on my Dapper Ubuntu Box.

This is a very stock install - no compiz, I have moved home to a seperate partition following asyiu's guide. I used Automatix to install codecs and nvidia drivers then uninstalled it.

Trying to download the runtime dependencies:
```
$ sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev gettext libfreetype6-dev 
```

I get this error:
> Reading package lists... Done
Building dependency tree... Done
gettext is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
 My sources.list file reads:
```


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main
[code]

I have done the following:
[code]sudo aptitude update && sudo aptitude upgrade
```
followed by:
```
sudo apt-get dist-upgrade
```

and the problem remains. I went into the package manager to see what was going on with libartsc0-dev and it says:
> 
"development files for the aRts sound system C support library
This package contains the header files needed to build applications that use the aRts sound daemon's C bindings.
This package is part of KDE, and a component of the KDE aRts module. See the 'kde' and 'arts' packages for more information." 


and has as a dependency "libglib2.0-dev" which is not installed and will not install. It will not install because it replaces libglib1.3-dev ***but!**** it conflicts with libglib1.3-dev which is ***not*** in the package manager or on my machine.

So I look up arts - I try to remove arts and it won't let me - it will break packages.

So I look up KDE and it's not installed and won't let me install it?!? On Kubuntu?!?

Is there any way to fix this? I can live without the game on this box - heck I'm supposed to work on this one anyway.

But this was going ***so*** good to. I don't want to have to start over, especially when as far as I know I haven't done anything to mess it up - this is the first compile I've tried on this box, everything else on here is from the repositories.
:cry:

edit - I found the answer on a mac forum for goodness sakes, it had a link to Kubuntu. There were no KDE addys in my sources list.

Why that didn't show up when I searched there I ain't got a clue.

Would not having KDE repositories in Kubuntu be considered a bug?

---

### Post by amohanty on 2006-11-05
Ok first try the following:
1. Fire up synaptic
2. Select Custom in the bottom left
3. Select Broken in the left panel
4. Right click on the pkg in the right panel and select remove completely

Once the broken stuff is removed, we can try to get what you want done.

AM

---

### Post by der_joachim on 2006-11-05
```
aptitude -f install
```

should do the trick.

---

