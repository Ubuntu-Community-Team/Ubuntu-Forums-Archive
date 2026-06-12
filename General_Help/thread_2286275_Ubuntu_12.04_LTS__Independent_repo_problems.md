---
title: "Ubuntu 12.04 LTS / Independent repo problems"
date: 2015-07-11
forum: General Help
---

### Post by simple_impulse on 2015-07-11
If I take out Independent repositories, my Ubuntu 12.04 LTS 32-bit updates and everything works.

But if Independent repos are selected in Update Manager, aptd dies in update and after that even apt-get commands fail.

I can correct the situation temporarily with

sudo rm /var/lib/apt/lists/* -vf

But if I re-do apt-get or use Update Manager with Independent repos on, the situation repeats.

Two questions:

How can I list what exactly my Ubuntu uses from Independent repos?
Is this related something else I could check? Both apt-get and dpkg are happy with databases if I update without Independent repos.

I have other machine with Ubuntu 12.04 LTS 64-bit. This problem does not affect that machine.

Any ideas?

---

### Post by v3.xx on 2015-07-11
You need to post the error messages.

---

### Post by Vladlenin5000 on 2015-07-11
> **v3.xx said:**
> You need to post the error messages.

+1

... And it isn't a all or nothing situation, i.e., one or more PPAs may have a problem, not all of them. Anyway, the error messages from ```
sudo apt-get update
``` should be enough to know which ones.

---

### Post by simple_impulse on 2015-07-11
When I click "Check" in Update manager when the situation is on:

---

Task cannot be monitored or controlled

The connection to the daemon was lost. Most likely the background daemon crashed.

Details

It seems that the daemon died.

---

All apt-get:s just stop during db read:

---

quantum@penguin:~$sudo apt-get update
[... lots of normal lines removed ...]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US              
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en          
Fetched 951 kB in 4s (193 kB/s)             
quantum@penguin:~$ ts... 90%

---

Another example:

---

quantum@penguin:~$ sudo apt-get install -f
quantum@penguin:~$ ts... 90%

---

I have tried:
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --configure -a

---

Only thing which restores the sanity of apt commands is

sudo rm /var/lib/apt/lists/* -vf

But of course next update (again) makes everything fail again.

---

### Post by v3.xx on 2015-07-11
Maybe something odd in your sources?  Please post
```
cat /etc/apt/sources.list
```
and your ppa's
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by simple_impulse on 2015-07-11
Sources:
```
# 



# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fi.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fi.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fi.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise universe
deb http://fi.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fi.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://fi.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://fi.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main
deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu precise main
deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu precise main
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu precise main
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu precise main
deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
deb http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu precise main
deb-src http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu precise main
deb http://ppa.launchpad.net/purplekarrot/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/purplekarrot/ppa/ubuntu precise main
deb http://ppa.launchpad.net/irie/openimageio/ubuntu precise main
deb-src http://ppa.launchpad.net/irie/openimageio/ubuntu precise main
deb http://ppa.launchpad.net/irie/blender/ubuntu precise main
deb-src http://ppa.launchpad.net/irie/blender/ubuntu precise main
# deb http://download.virtualbox.org/virtualbox/debian precise contrib
deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu precise main
deb http://ppa.launchpad.net/gnomebaker/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu precise main
deb http://ppa.launchpad.net/dimula73/krita/ubuntu precise main
deb-src http://ppa.launchpad.net/dimula73/krita/ubuntu precise main
deb http://ppa.launchpad.net/quadrispro/backports/ubuntu precise main
deb-src http://ppa.launchpad.net/quadrispro/backports/ubuntu precise main
deb http://ppa.launchpad.net/olci/ppa1/ubuntu precise main
deb-src http://ppa.launchpad.net/olci/ppa1/ubuntu precise main
deb http://ppa.launchpad.net/dns/sound/ubuntu precise main
deb-src http://ppa.launchpad.net/dns/sound/ubuntu precise main
deb http://ppa.launchpad.net/gnu-psychosynth-team/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/gnu-psychosynth-team/ppa/ubuntu precise main
deb http://ppa.launchpad.net/atareao/sunflower/ubuntu precise main
deb-src http://ppa.launchpad.net/atareao/sunflower/ubuntu precise main
deb http://ppa.launchpad.net/webupd8team/atom/ubuntu precise main
deb-src http://ppa.launchpad.net/webupd8team/atom/ubuntu precise main
deb http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu precise main
deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-daily/ubuntu precise main
```

PPAs:
```
/etc/apt/sources.list.d/aaron-haviland-cuda-4.0-natty.list
/etc/apt/sources.list.d/achadwick-mypaint-testing-natty.list
/etc/apt/sources.list.d/achadwick-mypaint-testing-precise.list
/etc/apt/sources.list.d/atareao-atareao-precise.list
/etc/apt/sources.list.d/chrysn-openscad-precise.list
/etc/apt/sources.list.d/clipgrab-team-ppa-natty.list
/etc/apt/sources.list.d/clipgrap-team-ppa-natty.list
/etc/apt/sources.list.d/dropbox.list
/etc/apt/sources.list.d/ferramroberto-java-natty.list
/etc/apt/sources.list.d/ferramroberto-vlc-natty.list
/etc/apt/sources.list.d/getdeb.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/gstreamer-developers-ppa-precise.list
/etc/apt/sources.list.d/hplip-isv-ppa-precise.list
/etc/apt/sources.list.d/irie-lmms-precise.list
/etc/apt/sources.list.d/jonoomph-openshot-edge-natty.list
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list
/etc/apt/sources.list.d/kubuntu-ppa-backports-precise.list
/etc/apt/sources.list.d/librecad-dev-librecad-daily-natty.list
/etc/apt/sources.list.d/libreoffice-ppa-precise.list
/etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-natty.list
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/neon-ppa-natty.list
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list
/etc/apt/sources.list.d/ogre-team-ogre-natty.list
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
/etc/apt/sources.list.d/scootersoftware.list
/etc/apt/sources.list.d/skype-wrapper-ppa-precise.list
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list
/etc/apt/sources.list.d/sun-java-community-team-sun-java6-natty.list
/etc/apt/sources.list.d/trebelnik-stefina-flowblade-precise.list
/etc/apt/sources.list.d/tualatrix-ppa-natty.list
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-natty.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-natty.list
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
/etc/apt/sources.list.d/webupd8team-sublime-text-2-precise.list
```

---

### Post by Bashing-om on 2015-07-11
simple_impulse; Hello;

allow me to respond. as your 1st responder is presently off-line.
A number of issues and possible issues with the sources list .
1st is the no-longer supported releases held in ' ls /etc/apt/sources.list.d/ ' If it is not 'precise' then disable all these other PPAs .

Next is how many duplications exist between the PPAs listed in '/etc/apt/sources.list.d/' and '/etc/apt/sources.list' ?
Be aware that the purpose of the 'sources.list.d' directory is to hold those 3rd party sources.

Then when the ppa's are straight, we verify that the maximum number of PPAs has not been reached:
```

ls /etc/apt/trusted.gpg.d | wc -l

```

[INDENT][INDENT]I hazzard to guess
[INDENT][INDENT][INDENT]what happens next[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by simple_impulse on 2015-07-11
@Bashing-om:

I didn't find any duplicates; those repos for Natty are before upgrade to Precise, but those are not selected (not showing in Update Manager). 

Command:
ls /etc/apt/trusted.gpg.d | wc -l

returned 0.

---

### Post by Bashing-om on 2015-07-11
simple_impulse; Yeah;

But, if those 'natty' repos are still in an active state, the system is going to act on them, and as they are no longer supported, the reaction will be very adverse !

Let's look at the condition:
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

as a step in the direction to get the package manager correct.

[INDENT][INDENT]small steps, one at a time
[/INDENT][/INDENT]

---

### Post by simple_impulse on 2015-07-12
Good morning! Mystically the problem vanished. It seems that some repository sent yesterday faulty lists and today the situation is corrected. Of course I have no proof, but it seems unlikely that the fault just vanished otherwise. It was not session dependent either, because I rebooted the machine several times yesterday... Maybe I should keep this open for some time, just to make sure that the situation doesn't repeat tomorrow.

Thanks for your answers, all, I do hope this is solved! But let's wait for some time, I'm a bit nervous. I am not used to problems correcting themselves.

---

### Post by Vladlenin5000 on 2015-07-12
Actually server side issues usually don't last for long. You know, people complain...
I'm not saying it was the case here but I've occasionally experienced update errors that were corrected the next day.

---

### Post by Bashing-om on 2015-07-12
simple_impulse; Yeah;

> **Vladlenin5000 said:**
> Actually server side issues usually don't last for long. You know, people complain...
I'm not saying it was the case here but I've occasionally experienced update errors that were corrected the next day.


Same same experience, maybe just a case of the mirror catching up .

We wait and see ->
[INDENT][INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT][/INDENT]

---

### Post by simple_impulse on 2015-07-14
Curiouser and curiouser.

The problem came back, BUT: this time removing the directory contents and issuing all those cleaning commands from command line and then apt-get update solved the problem. I'm beginning to suspect apt-get or aptd but that must be insane; so much used apps and daemons can't have this kind of problems. Maybe I should do more system checking. HDD at least seems to be OK. I'll report if I find something.

---

### Post by simple_impulse on 2015-07-16
...today the situation repeated, but this time the cleaning and removing didn't help. I don't have time just now to investigate, but I really hope the updates work later. I'm a bit curious, what kills aptd during update?

---

### Post by simple_impulse on 2015-07-16
...aaand... evening updates (only Flash installer) corrected the situation with no effort on my side. Honestly, there are gremlins in this system.

---

### Post by Bashing-om on 2015-07-16
simple_impulse; Well ..

Maybe all related to "Flash" ? As you may be aware there did exist a vulnerability(s) and Flash has been blocked.
I do not run Flash, so Am not keeping current on what is taking place.

[INDENT][INDENT]no doubt though
[INDENT][INDENT][INDENT]strange things can happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by simple_impulse on 2015-07-18
I did suspect Flash installer too, especially because it's different from others; it's actually a script, which downloads the plugin itself during update process. But I don't have proof. It is possible that the download script does something which leaves apt database somehow in unstable condition.

I'll let you know if I find out new details. Today update check went normally (and there wasn't any updates).

There are many (security and functional) reasons to get rid of Flash but I have so many graphical web based interfaces in use that I am worried that the change could cause other problems.

---

