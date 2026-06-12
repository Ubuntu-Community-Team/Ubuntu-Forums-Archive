---
title: "Software Sources Problems"
date: 2008-02-22
forum: General Help
---

### Post by dieselpower on 2008-02-22
I have been running Gutsy on my desktop since 2 days after it was released. It worked great for about two weeks, when for an unknown reason it started having problems with apt. I have not been able to upgrade or install some packages, it says "_E: Package pkg-name has no installation candidate_". I have played with many different sources.list and have never resolved the problem. I just installed Gutsy on my laptop today and it's working perfectly, so I copied the sources.list to my desktop, updated without errors, and still have uninstallable packages. Is there some other part of apt that needs to be dumped and re-loaded?? Why would it be doing this?

---

### Post by taurus on 2008-02-22
Why don't you post your /etc/apt/sources.list then?

```
cat /etc/apt/sources.list
```

---

### Post by dieselpower on 2008-02-22
Standard stuff, and the exact same list works dandy on the laptop.

```

#deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by taurus on 2008-02-22
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
What package are you trying to install anyway?  You can also use synaptic in System -> Administration to Search for it and see if you can install it from there.

---

### Post by dieselpower on 2008-02-23
I want to install Audacity ATM, However,
```

audacity: Depends: libwxgtk2.4-1 (>= 2.4.5.1ubuntu2) but it is not going to be installed

```
So, just fer kicks, apt-get install libwxgtk2.4-1,
```

libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable

```

I have been working around this by getting packages off of launchpad and hand installing them, but that gets old real quick. Might as well run Red Hat 7.2! Heh, that reminds me of working for pizza in the lab and the Lucky Numbers! Bet not too many others on here know anything about that! Anyway, this beats me, any other ideas? I DO NOT want to reinstall.

---

### Post by dieselpower on 2008-02-23
Also, I should note that I have to "apt-get update" over a SSH SOCKS tunnel because my ISP blocks/mangles too much stuff and the keys dont match if I do it over clear HTTP. It works just fine from a friends DSL line. It always works over HTTP on the first time after install, but after that it errors on the keys unless I run it on SOCKS to one of my servers.

Hey, I need to buy some _beans_, who has the best ones on ebay?

---

### Post by oldos2er on 2008-02-23
Have you tried enabling the deb-src repositories you currently have commented out?

---

### Post by zvacet on 2008-02-23
Did you tried what Taurus adviced to you(install with synaptic)?That is easy way t odo it.Other way is to go to the [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and type package name you are looking for.Make sure that you download and install dependencies (marked with red ball) first.Maybe some of dependencies you allready have installed so look in synaptic for that.No need to download something you allready have.

---

### Post by dieselpower on 2008-02-23
synaptic has the same problems. and I like the command line better when it works, 'cause when it doesn't work, you know why. If you'll read, you would find out I have been downloading by hand, that works for a few now and then.. It's just that I need this fixed because that method is getting unmanagable.

---

### Post by dieselpower on 2008-02-23
I just enabled all the deb-src lines, and still have the same problem. But I just found what causes this, and now I need some help fixing it. Last night I upgraded my fresh install on my laptop. 190 some packages, and it downloaded about 70% of them before the connection crapped out. It would not resume, so I clicked cancel all changes and at the next screen it said update complete even though it had not installed any updates yet. Then it said a new version was available, I could upgrade (from gutsy) to gutsy, so I cancelled that. Now there is nothing to upgrade, and some packages are no longer installable. How do I get out of this?

---

### Post by dieselpower on 2008-02-23
Please help, every ubuntu box around here has this problem, The updates cannot download in one night, so they get interupted, adept-updater MARKS ALL PACKAGES UPDATED, even though it only downloaded some of them, nevermind unpacking and installing. This royally screws the whole apt system, command line upgrades show that the package is the latest version, even though it is not., and half the software is UNINSTALLABLE. subsequent apt-get updates DO NOT HELP. I am running the default ubuntu sources.list with everything enabled, --it worked perfectly before the borked upgrade.

So now I'm missing half my sources, how do I get them back?
After they are back, how do I force re-install  every package on the system?

If there is no way out of this, I'm putting gentoo back on every system out here, it works.

---

### Post by zvacet on 2008-02-24
Try to change to main server,because it can be your local server thing.After that run 

```
sudo apt-get -f install
```

and you can try for uninstallable

```
sudo apt-get install --reinstall packagename
```

---

### Post by dieselpower on 2008-02-24
It thinks everything is fine.
```
lawrence@lawrence:~$ sudo apt-get -f install
[sudo] password for lawrence:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I have not upgraded anything in about a month, but I apt-get update every day.
```
lawrence@lawrence:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Here is where the problem comes in.
```
lawrence@lawrence:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
```

And here, read the whole thing there are three operations here.
```
lawrence@lawrence:~$ sudo apt-get install audacity
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  audacity: Depends: libwxgtk2.4-1 (>= 2.4.5.1ubuntu2) but it is not going to be installed
E: Broken packages
lawrence@lawrence:~$




lawrence@lawrence:~$ sudo apt-get install libwxgtk2.4-1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
E: Broken packages




lawrence@lawrence:~$ sudo apt-get install libglib1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libglib1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libglib1.2 has no installation candidate

```

This all works fine on a freshly installed machine. It only happens after an interupted upgrade.

---

### Post by dieselpower on 2008-02-24
**FIXED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

I did an apt-get update with an empty sources.list, then copied the sources.list back and did an update again, everything is working properly now. Thanks!!!!!

---

### Post by kojo on 2008-02-25
Wow! Thanks for your post.  I just fixed this exact problem using your advice (disable repositories in sources.list the sudo apt-get update, reenable repos and sudo apt-get update again).

Ubuntu Server Edition 7.10 64 bit
thanks!

---

