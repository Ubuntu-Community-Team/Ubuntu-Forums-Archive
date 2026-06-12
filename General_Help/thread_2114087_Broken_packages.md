---
title: "Broken packages"
date: 2013-02-09
forum: General Help
---

### Post by CinoxFellpyre on 2013-02-09
```
The following packages have unmet dependencies:

libgbm1: Depends: libdrm-nouveau2 (>= 2.4.34) but it is not installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
         Depends: libudev0 (>= 147) but 175-0ubuntu9.2 is installed
```

Tried to use Ubuntu Software Center and get "Needs to be repaired"

Kubuntu 12.04

Also this may be a symptom but Skype cannot acess mic without me using sudo.

---

### Post by dino99 on 2013-02-09
looks like some packages conflict from non genuine source(s) (ppa)
if its the case, then use ppa-purge, update and retry to fix the dependencies.

---

### Post by CinoxFellpyre on 2013-02-09
> **dino99 said:**
> looks like some packages conflict from non genuine source(s) (ppa)
if its the case, then use ppa-purge, update and retry to fix the dependencies.
Ok I've never done this before...

Can you post the lines?

---

### Post by CinoxFellpyre on 2013-02-11
bump

---

### Post by iamkuriouspurpleoranj on 2013-02-11
Do you have synaptic package manager installed?

If so, open it up and click on Settings -> Filters -> Broken and then click "OK"

Then click on Edit -> Fix Broken Packages and click on "apply"

If that doesn't sort it out, let me know.

---

### Post by CinoxFellpyre on 2013-02-11
E: /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau1a 2.4.41+git1301220934.303ca3~gd~p

Same garbage.

---

### Post by iamkuriouspurpleoranj on 2013-02-12
Hmm... Try sudo apt-get clean. That will clear the cache.

---

### Post by schragge on 2013-02-12
You've installed a driver for your graphic card from some PPA (probably from [ppa:oibaf/graphics-drivers]("https://launchpad.net/%7Eoibaf/+archive/graphics-drivers")). Now, an updated package for this driver from *precise-updates* (libdrm-nouveau2) tries to get installed, but cannot because the two packages conflict. Since some other package updates in *precise-updates* depend on that package, failure to install it holds them up.

You can either deinstall the package from PPA to make way for the official one, or set the packages from PPA on hold.

Also look at [thread=2114567]this thread[/thread]. But please don't rush to do what I recommend there: it's not quite your situation. First, let us know which of the two options described above do you prefer.

---

### Post by CinoxFellpyre on 2013-02-12
I'll go for the former, the deinstall.

Only problem is I don't know what one I need to uninstall.

---

### Post by schragge on 2013-02-12
From the PPA page:
> To revert to standard Ubuntu drivers type the following in a prompt shell:
```

$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa:oibaf/graphics-drivers

```

---

### Post by CinoxFellpyre on 2013-02-12
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgbm1 : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not going to be installed
 ppa-purge : Depends: aptitude but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```And what's even worse is I now have well, see attached.

EDIT: So after trying to get window manager back on (which it wasn't for some reason) I got this.

CuddlyZebesian@cinoxfellpyre-Satellite-L305:~$ kwin
The program 'kwin' is currently not installed.  You can install it by typing:
sudo apt-get install kde-window-manager
CuddlyZebesian@cinoxfellpyre-Satellite-L305:~$ sudo apt-get install kde-window-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgbm1 : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

At this point I think libdrm-nouveau2 is completely ruining everything and I'm about ready to remove the damn package, but I don't know myself what it is or does.

---

### Post by schragge on 2013-02-12
Well, try
```

sudo apt-get clean
sudo apt-get -d --no-upgrade install ppa-purge aptitude
sudo dpkg --force-all -i /var/cache/apt/archives/*.deb
sudo ppa-purge ppa:oibaf/graphics-drivers
sudo apt-get upgrade

```

---

### Post by CinoxFellpyre on 2013-02-12
```
CuddlyZebesian@cinoxfellpyre-Satellite-L305:~$ sudo apt-get -d --no-upgrade install ppa-purge aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.46.1 (>= 1.46.1-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
 libgbm1 : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

EDIT: Ok I found this other package that was libdrm-ltsq-nouveau2. With it I was able to get ppa-purge and whatnot on there, and now running the rest of the commands, I'll update when needed.

EDIT EDIT: Well everything went well but I got
```
CuddlyZebesian@cinoxfellpyre-Satellite-L305:~$ sudo ppa-purge ppa:oibaf/graphics-drivers
Updating packages lists
PPA to be removed: oibaf graphics-drivers
Warning:  Could not find package list for PPA: oibaf graphics-drivers
```

I probably don't have it on there at all.

---

### Post by CinoxFellpyre on 2013-02-12
Well I restarted my PC and everything seems to be normal now.

Except Skype.

---

