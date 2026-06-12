---
title: "How to reinstall ALL printer services &amp; functions"
date: 2020-05-22
forum: General Help
---

### Post by jimmyman on 2020-05-22
Okay I've been through the sea of internet help and have botched up my printer services, functions, cups, everything. LOL.

I'm running xubuntu 18.04.4 

How do I reinstall EVERYTHING back to default that deals with my printer as if it were a fresh install?

---

### Post by CelticWarrior on 2020-05-22
Reinstall the OS is my suggestion. Then, if you find any problem, better ask about it first.

---

### Post by TheFu on 2020-05-22
I can't say this won't do any harm, but if you have nothing to lose, you can 
**sudo apt purge cups**
then verify that everything under /etc/cups/ is gone.  Wipe the directory.  There could be some files in your HOME for cups.  Delete those too, where ever they are. I'd look in ~/.config/  I didn't find any in my setup, but I barely print and have a fresh install. The printer setup might be shoveled into some gtk DB.  I hate when programs do that. gconf ... 
Might be worth running **sudo apt autoremove** too.

Then **sudo apt install cups**

There might be other packages related to cups. I found about 25 of them.  No clue if this will help or not. I've never had that issue the last 20+ yrs.

I've never had a network printer here and won't have any wifi printers.  At work, we have lots of network printers, but they all accept jobs only from print queue servers, not desktops.  My home printers are USB connected to a central print server. Setting up printers to go through the print server is pretty bonehead.  I just point at the print server, choose the IPP protocol and pick the driver from the huge list provided. Its been that way for since 10.04.  Prior to that, printers were a hassle.

---

### Post by VMC on 2020-05-22
If you log into the cups admin page, what does it show. Can you manipulate your settings:
[http://localhost:631/admin/](http://localhost:631/admin/)

---

### Post by jimmyman on 2020-05-22
> **VMC said:**
> If you log into the cups admin page, what does it show. Can you manipulate your settings:
[http://localhost:631/admin/](http://localhost:631/admin/)

It just says page can't be reached.

> **TheFu said:**
> I can't say this won't do any harm, but if you have nothing to lose, you can 
**sudo apt purge cups**
then verify that everything under /etc/cups/ is gone.  Wipe the directory.  There could be some files in your HOME for cups.  Delete those too, where ever they are. I'd look in ~/.config/  I didn't find any in my setup, but I barely print and have a fresh install. The printer setup might be shoveled into some gtk DB.  I hate when programs do that. gconf ... 
Might be worth running **sudo apt autoremove** too.

Then **sudo apt install cups**

There might be other packages related to cups. I found about 25 of them.  No clue if this will help or not. I've never had that issue the last 20+ yrs.

I've never had a network printer here and won't have any wifi printers.  At work, we have lots of network printers, but they all accept jobs only from print queue servers, not desktops.  My home printers are USB connected to a central print server. Setting up printers to go through the print server is pretty bonehead.  I just point at the print server, choose the IPP protocol and pick the driver from the huge list provided. Its been that way for since 10.04.  Prior to that, printers were a hassle.


I tried to remove cups and it wasn't found.  Then I tried the install and this is what I got.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cups is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cups-filters-core-drivers cups-daemon cups-filters


E: Package 'cups' has no installation candidate
```

---

### Post by VMC on 2020-05-22
Could means cups not installed.

---

### Post by jimmyman on 2020-05-22
```
sudo apt-get install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cups is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cups-filters-core-drivers cups-daemon cups-filters


E: Package 'cups' has no installation candidate
```

---

### Post by VMC on 2020-05-22
status:```
systemctl status org.cups.cupsd.service
```

---

### Post by jimmyman on 2020-05-22
> **VMC said:**
> status:```
systemctl status org.cups.cupsd.service
```

Unit org.cups.cupsd.service could not be found.



Very puzzled on this one.

---

### Post by VMC on 2020-05-23
Here's mine now:
```
$ systemctl status org.cups.cupsd.service
&#9679; org.cups.cupsd.service - CUPS Scheduler
     Loaded: loaded (/usr/lib/systemd/system/org.cups.cupsd.service; enabled; vendor preset: disabl>
     Active: active (running) since Fri 2020-05-22 21:03:15 PDT; 15min ago
TriggeredBy: &#9679; org.cups.cupsd.path
             &#9679; org.cups.cupsd.socket
       Docs: man:cupsd(8)
   Main PID: 877 (cupsd)
     Status: "Scheduler is running..."
      Tasks: 1 (limit: 9388)
     Memory: 3.6M
     CGroup: /system.slice/org.cups.cupsd.service
             &#9492;&#9472;877 /usr/bin/cupsd -l

May 22 21:03:15 vmc-tc885 systemd[1]: Starting CUPS Scheduler...
May 22 21:03:15 vmc-tc885 systemd[1]: Started CUPS Scheduler.
```
Here's what I needed to do, to get it started:
```
sudo systemctl enable org.cups.cupsd.service
sudo systemctl start org.cups.cupsd.service
```

---

### Post by DuckHook on 2020-05-23
Before installing any pkg, you *must* first: ```
sudo apt update
``` In your case, after updating, post back results of: ```
apt policy cups
```
You mentioned that you monkeyed around with your system something awful. Try to recount the things you did. Post them point by point. Did you do anything to your sources.list? Please post results of: ```
cat /etc/apt/sources.list
```

Last but not least, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by jimmyman on 2020-05-23
Yes, did the sudo apt update (fairly experienced in Linux)


```


apt policy cups

cups:
  Installed: (none)
  Candidate: (none)
  Version table:

```

Also

```


cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ bionic restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates restricted universe multiverse


```

---

### Post by jimmyman on 2020-05-23
> **VMC said:**
> 
Here's what I needed to do, to get it started:
```
sudo systemctl enable org.cups.cupsd.service
sudo systemctl start org.cups.cupsd.service
```

Okay, both of these failed. 

```

Failed to enable unit: Unit file org.cups.cupsd.service does not exist.
Failed to start org.cups.cupsd.service: Unit org.cups.cupsd.service not found.




```

---

### Post by DuckHook on 2020-05-23
You have a severely broken *sources.list* file and you did not carry out the following instructions: > **DuckHook said:**
> &#8230;You mentioned that you monkeyed around with your system something awful. Try to recount the things you did. Post them point by point&#8230;
Please post these now.

Also, confirm that you have backed up all of your important data.

Here is a virgin Bionic sources.list file:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```
You will need to replace the contents in the one you have with the contents above. Make sure that the resulting file is owned by root. It won't run if owned by you or any other normal user. Must be root. The best say to replace the above is to:

[list=1]
[*]Open a terminal and: ```
sudo nano /etc/apt/sources.list
```
[*]Delete all contents
[*]Copy and paste the above contents into nano. In nano, pasting is done with <Ctrl>+<Shift>+<V>
[*]Save <Ctrl>+<o> and exit nano <Ctrl>+<x>
[*]Reboot
[/list]
When system comes back up again, try to install cups: ```
sudo apt update && sudo apt install cups
```

:!:**A really big caveat**:!: 
You have not told us what steps you took that led to this. In my experience, a *sources.list* file as broken as yours usually indicates that you did a dozen other things that have taken your system far beyond a stable, default state. Personally, I feel as CelticWarrior does: you are better off reinstalling after backing up your important data. But the choice is yours.

---

### Post by jimmyman on 2020-05-23
Okay, on 

```

sudo apt install cups

```

I get

```

sudo apt install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 cups : Depends: libcups2 (= 2.2.7-1ubuntu2.8) but 2.3.1-11 is to be installed
        Depends: libcupscgi1 (>= 1.4.2) but it is not going to be installed
        Depends: libcupsmime1 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsppdc1 (>= 1.4.0) but it is not going to be installed
        Depends: cups-core-drivers (>= 2.2.7-1ubuntu2.8)
        Depends: cups-daemon (>= 2.2.7-1ubuntu2.8)
        Recommends: printer-driver-gutenprint but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by DuckHook on 2020-05-23
From a practical perspective, there really is no point in continuing to chase this unicorn. You won't or can't tell us what you did to break it and I have already noted:> **DuckHook said:**
> :!:**A really big caveat**:!: 
You have not told us what steps you took that led to this. In my experience, a *sources.list* file as broken as yours usually indicates that you did a dozen other things that have taken your system far beyond a stable, default state. Personally, I feel as CelticWarrior does: you are better off reinstalling after backing up your important data…Another forum member may have more experience dealing with an install this broken, but I'm afraid that I can be of no further help.

---

### Post by VMC on 2020-05-24
"...no point in continuing to chase this unicorn." Made me laugh.

Jimmyman, not sure of your Linux tenure, but in the future if you want to experiment, first back up your system. Then hack away to your hearts content.

---

### Post by DuckHook on 2020-05-24
> **VMC said:**
> …in the future if you want to experiment, first back up your system. Then hack away to your hearts content.
&#8593;+1

Or do such hacking in a VM.

---

### Post by jimmyman on 2020-05-24
Honestly it was a snowball.  Tried this to fix, that to fix... life happens.  Then this, then that the next day.  Then this and that the next day.  Got busy, weeks pass... Then it continued for a few more fixes.  LOL.   Okay, looks like I'll have to just update to a new version.

---

