---
title: "Software center and synaptic both not loading and throwing up an error."
date: 2013-06-10
forum: General Help
---

### Post by Overlooks on 2013-06-10
I just downloaded Ubuntu 12.04 the other day after using windows for as long as I can remember so I'm a complete newb. Now, as the title says, both Ubuntu Software Center and Synaptic Package Manager refuse to load throw this error: "E:Type 'net/weather-indicator-team/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list" I can't seem to delete it and I can't get root access like what I've seen suggested for similar problems. What makes this even worse is when I shut my laptop down, I have to turn it on and off a few (10+ times) before it'll boot, instead giving me the option of recovery mode and memory testing. It won't load in recovery mode during all that either so needless to say, I'm at a complete loss as to what to do and I hate it because I want to enjoy Linux but at this point I'm not too sure about it...

Thanks in advance.

---

### Post by ohnonot on 2013-06-10
this sounds like 2 unrelated problems.

for the first: what happens when you type 'sudo gedit /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list' in a terminal?

if the file actually opens (as it should), post its contents here.

---

### Post by greatsirkain on 2013-06-10
if you launch synaptic from a terminal with sudo it will be root

```
sudo synaptic
```

Edit: ctrl+alt+t to open a terminal window (don't know how new you are from windows :P )

---

### Post by Overlooks on 2013-06-10
> **ohnonot said:**
> this sounds like 2 unrelated problems.

for the first: what happens when you type 'sudo gedit /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list' in a terminal?

if the file actually opens (as it should), post its contents here.

This is what comes up:

> net/weather-indicator-team/ppa/ubuntu precise main #A weather indicator for Ubuntu's Indicator Applet

> **greatsirkain said:**
> if you launch synaptic from a terminal with sudo it will be root

```
sudo synaptic
```

Edit: ctrl+alt+t to open a terminal window (don't know how new you are from windows :P )


This is what it says when I do that:

> E: Type 'net/weather-indicator-team/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.listE: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



Edit: This is also preventing me from downloading stuff through the terminal and says this:
> E: Type 'net/weather-indicator-team/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.listE: The list of sources could not be read.


---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]Overlooks; Hi ! Welcome to the forum .

As a new user to linux keep in mind "a different way of thinking"... We are going to keep this as simple as possible and deal with only one situation at a time per thread.
To address the main issue; errors from synaptic and Software Center; 
The file "sources.list" located in the file hierarchy at /etc/apt/ is the main database controlling acquisition of application packages on the ubuntu operating systems. Let us see that that file is present ...
For the more expeditious method to display this information resort to the Command Line Interface; -for us to see-
key combo ctl+alt+t yields a terminal for this interface.
In the terminal type:
```
ls -la /etc/apt/sources.list
``` which list (ls) with option l (long) and (a) all, on the path /etc/apt/ to the file "sources.list"
to see if indeed that required file exist... 
Post the out put of the command - between code (#) tags - top of post- back to this thread.

The error says that there is a fault in this file at line one... so let us look at that file. As It is a system file we must have administrative authority to effect any change to that file and further, we are going to use a GUI tool to do so called gedit. 
```
gksudo gedit /etc/apt/sources.list
``` gksudo is the graphical equivalent of "sudo" -for elevate privileges, activates the editor (gedit) and opens the file "sources.list"... to that end we are not presently prepared to do an edit to that file... all we want to do is "look" at it and see what is to be done. So -> CLI
```
cat /etc/apt/sources.list
``` cat == contentonate (sp); output a files content
and post that out put back to us.

Aside: Your system maintains a database of all terminal commands, this documentation is accessed from terminal with:
```
man <command_name>
```
examples man ls or man cat
addition information may be available from the manual system with:
```
info <command_name>
``` .....
[/COLOR][INDENT=2][COLOR=#000000]
further advise pending what the "sources.list" file contains.
 [/COLOR][/INDENT]

---

### Post by Overlooks on 2013-06-10
entering the first code gives this:
```
-rw-r--r-- 1 root root 3369 Jun 10 16:24 /etc/apt/sources.list
```

This was in the sources.list file:
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main#
```

I didn't see the cat /etc/... code, I apologize but this is what came up when entered:
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


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
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]Overlooks; Hey,

My apologies to you ... I failed to read the error in your first post properly....
we are looking at:
[/COLOR]> [COLOR=#000000]on line 1 in source list /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list" [/COLOR][COLOR=#000000]
so let's look properly at what is contained in that directory:
```
ls -la /etc/apt/sources.list.d/
``` to find the offending file to edit is there.
And to look at that file that is to be edited:

```
cat /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list
```
Post that output back for advise on editing the file in the text editor "gedit"
[/COLOR][INDENT][COLOR=#000000]
3 steps forward on 1 back

[/COLOR][/INDENT]

---

### Post by Overlooks on 2013-06-10
Entering the first code brings this:
```
ls: cannot access /etc/apt/sources/list.d/: No such file or directory
```

entering the second just says this in the terminal:
```
net/weather-indicator-team/ppa/ubuntu precise main #A weather indicator for Ubuntu's Indicator Applet

```

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]Overlooks;
You did a miss type in the ls command... no biggy as the second command to "cat" that file is successful ...
and yeah... that line is not as per required formatting. Let me see what I can find out to afix the proper IP//
or perhaps a proper way to (re)generate that file.
in the mean time... lets see if there exist a backup of that file in that directory
Terminal command:
```
ls -la /etc/apt/sources.list.d/
``` to list all the files within the directory "sources.list.d"

Next lesson maybe in regards to all the information detailed in the "ls" command.
[/COLOR][INDENT=2][COLOR=#000000]
keep on keep'n on [/COLOR][/INDENT]

---

### Post by Overlooks on 2013-06-10
My apologies for the mistype I wish I could copy and paste into terminal but when I do it shows "^V" but I digress.

This is what comes up when I type it in (and I double checked my typing this time ;)):
```
total 92drwxr-xr-x 2 root root 4096 Jun 10 16:24 .
drwxr-xr-x 6 root root 4096 Jun 10 16:24 ..
-rw-r--r-- 1 root root    0 Jun  9 22:52 atareao-atareao-precise.list
-rw-r--r-- 1 root root   71 Jun  9 22:52 atareao-atareao-precise.list.save
-rw-r--r-- 1 root root    0 Jun  9 22:52 atareao-indicators-precise.list
-rw-r--r-- 1 root root   74 Jun  9 22:52 atareao-indicators-precise.list.save
-rw-r--r-- 1 root root    0 Jun  9 22:52 cooperjona-stormcloud-precise.list
-rw-r--r-- 1 root root   94 Jun  9 22:52 cooperjona-stormcloud-precise.list.save
-rw-r--r-- 1 root root  176 Jun 10 16:24 google-chrome.list
-rw-r--r-- 1 root root  176 Jun 10 16:24 google-chrome.list.save
-rw-r--r-- 1 root root   95 Jun 10 16:24 loneowais-gmailwatcher.dev-precise.list
-rw-r--r-- 1 root root   95 Jun 10 16:24 loneowais-gmailwatcher.dev-precise.list.save
-rw-r--r-- 1 root root  167 Jun 10 16:24 private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list
-rw-r--r-- 1 root root  167 Jun 10 16:24 private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list.save
-rw-r--r-- 1 root root  157 Jun 10 16:24 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root  157 Jun 10 16:24 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root    0 Jun  9 22:52 pywapi-devel-ppa-precise.list
-rw-r--r-- 1 root root   72 Jun  9 22:52 pywapi-devel-ppa-precise.list.save
-rw-r--r-- 1 root root  128 Jun 10 16:24 rvm-smplayer-precise.list
-rw-r--r-- 1 root root  112 Jun 10 16:24 steam.list
-rw-r--r-- 1 root root  112 Jun 10 16:24 steam.list.save
-rw-r--r-- 1 root root  130 Jun 10 16:24 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root  130 Jun 10 16:24 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root  134 Jun 10 16:24 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Jun 10 16:24 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  102 Jun 10 16:24 weather-indicator-team-ppa-precise.list
-rw-r--r-- 1 root root  102 Jun 10 16:24 weather-indicator-team-ppa-precise.list.save

```

---

### Post by Bashing-om on 2013-06-10
Overlooks; Hey,
I Have my problems to on miss typing ... fingers get crossed with mind alla the time...

on topic: ok we got a backup file for what we are looking at so:
```
cat /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list.save
```

And from the looks of that directory, I should not be handling you with kid gloves, you have been around.
And I want to know the current status of the installation of "indicator-weather" before proceeding.
```
dpkg -l indicator-weather
```

[INDENT][INDENT]one more step[/INDENT][/INDENT]

---

### Post by Overlooks on 2013-06-10
Yeah, I just went crazy downloading and uninstalling it trying to get some weather notifier working until it was all messed up haha


this is what comes up:
```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  indicator-weat <none>         (no description available)

```

---

### Post by Bashing-om on 2013-06-10
Overlooks;

That output says there are problems... so let's clear the decks and then look at our status overall before doing anything else.
remove the indicator-weather config files:
```
sudo rm /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list
sudo rm /etc/apt/sources.list.d/weather-indicator-team-ppa-ppa-precise.list.save

```
And to remove the application (so it can be re-installed properly):
```
sudo apt-get install ppa-purge
sudo ppa-purge weather-indicator-team-ppa-precise

```

And IF that runs successfully update our database:
```

sudo apt-get update
sudo apt-get upgrade
```

With a stable foundation, we will proceed to install the weather app.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by Overlooks on 2013-06-10
It came up with this:
```
Updating packages listsPPA to be removed: weather-indicator-team-ppa-precise ppa
Warning:  Could not find package list for PPA: 
weather-indicator-team-ppa-precise ppa

```

but it opened update manager automatically and updated 6 things so I guess it half worked?

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks; shucks...
I recon I "guessed" the name of the ppa wrong... try:
[/COLOR]```
sudo ppa-purge weather-indicator
```

and yeah ...things are improving... gotta clean up weather-indicator prior to re-installing it. Why ? Because I do not know how it will be handled if we try and reinstall over a broken package installed through a ppa.[INDENT]
stepp'n but very small

[/INDENT]

---

### Post by Overlooks on 2013-06-11
I didn't mean for the last post to sound condescending in the closing statement, I apologize.

I tried that name and even went and tried a few other variations to no avail. Is there a way I could go through folders to find the name and then remove it from there either by deleting or through the terminal?

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks; 
This is ubuntu ...there is always a way ... try:
```
dpkg -l grep "weather*"
```
which I expect returns "weather-indicator" ,sooo ->
try 
```
sudo find / -name "weather*"
``` see if we get a solid result.
Another way ! synaptic, have you got synaptic installed ?
[INDENT=2]
we be look'n

[/INDENT]

[/COLOR]

---

### Post by Overlooks on 2013-06-11
Nope, but I assume it's telling me to download grep?

```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.10-1         GNU grep, egrep and fgrep
No packages found matching weather*.

```

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks;
well that output tells us that weather-indicator is no longer installed ... surprised as I thought the purge command failed !
see my edit though...and what does the "find command return ?
if you have synaptic installed ... best option in the world to look at packages.
[/COLOR][INDENT][COLOR=#000000]
hey we stepp'n now

[/COLOR][/INDENT]

---

### Post by Overlooks on 2013-06-11
Find gives this which was so long that I couldn't even see what I typed in so who knows what else there is but it seems like a bunch of random files for icons and stuff:
```
/usr/share/icons/gnome/24x24/status/weather-clear-night-050.png/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-060.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-140.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-340.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-270.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-030.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-070.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-130.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-280.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-120.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-200.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-260.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-230.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-330.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-110.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-320.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-010.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-040.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-310.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-020.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-000.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-200.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-070.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-190.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-110.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-090.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-210.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-290.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-170.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-280.png
/usr/share/icons/gnome/24x24/status/weather-clear-night-120.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-080.png
/usr/share/icons/gnome/24x24/status/weather-few-clouds-night-210.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-230.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-130.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-150.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-100.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-300.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-350.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-170.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-300.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-220.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-010.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-160.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-160.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-260.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-290.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-240.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-000.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-150.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-090.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-050.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-250.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-060.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-250.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-140.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-080.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-040.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-240.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-330.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-350.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-100.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-270.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-190.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-220.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-320.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-020.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-310.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-030.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-340.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-050.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-060.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-140.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-340.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-270.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-030.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-070.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-130.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-280.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-120.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-200.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-260.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-230.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-330.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-110.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-320.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-010.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-040.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-310.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-020.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-000.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-200.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-070.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-190.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-110.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-090.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-210.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-290.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-170.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-280.png
/usr/share/icons/gnome/32x32/status/weather-clear-night-120.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-080.png
/usr/share/icons/gnome/32x32/status/weather-few-clouds-night-210.png
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-260.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-260.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-050.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-170.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-000.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-250.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-010.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-090.svg
/usr/share/icons/gnome/scalable/status/weather-showers-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-300.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-030.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-040.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-300.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-250.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-100.svg
/usr/share/icons/gnome/scalable/status/weather-fog-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-330.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-000.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-070.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-160.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-290.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-240.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-320.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-340.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-330.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-070.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-190.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-060.svg
/usr/share/icons/gnome/scalable/status/weather-snow-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-210.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-270.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-220.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-090.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-080.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-350.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-showers-scattered-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-140.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-050.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-240.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-350.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-230.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-310.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-160.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-210.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-280.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-020.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-270.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-040.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-010.svg
/usr/share/icons/gnome/scalable/status/weather-clear-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-120.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-020.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-230.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-170.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-030.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-150.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-080.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-280.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-200.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-290.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-320.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-100.svg
/usr/share/icons/gnome/scalable/status/weather-overcast-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-severe-alert-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-340.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-310.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-140.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-120.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-150.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-130.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-200.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-110.svg
/usr/share/icons/gnome/scalable/status/weather-few-clouds-night-190.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-130.svg
/usr/share/icons/gnome/scalable/status/weather-storm-symbolic.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-220.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-110.svg
/usr/share/icons/gnome/scalable/status/weather-clear-night-060.svg
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-230.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-130.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-150.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-100.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-300.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-350.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-170.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-300.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-220.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-010.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-160.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-160.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-260.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-290.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-240.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-000.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-150.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-090.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-050.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-250.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-060.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-250.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-140.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-080.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-040.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-240.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-330.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-350.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-100.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-270.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-190.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-220.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-320.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-020.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-310.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-030.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-340.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-050.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-060.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-140.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-340.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-270.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-030.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-070.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-130.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-280.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-120.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-200.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-260.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-230.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-330.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-110.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-320.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-010.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-040.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-310.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-020.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-000.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-200.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-070.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-190.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-110.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-090.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-210.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-290.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-170.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-280.png
/usr/share/icons/gnome/16x16/status/weather-clear-night-120.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-080.png
/usr/share/icons/gnome/16x16/status/weather-few-clouds-night-210.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-230.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-130.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-150.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-100.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-300.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-350.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-170.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-300.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-220.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-010.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-160.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-160.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-260.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-290.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-240.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-000.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-150.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-090.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-050.png
/usr/share/icons/gnome/22x22/status/weather-clouds.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-250.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-060.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-250.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-140.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-080.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-040.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-240.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-330.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-350.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-100.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-270.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-190.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-220.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-320.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-020.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-310.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-030.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-340.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-050.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-060.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-140.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-340.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-270.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-030.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-070.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-130.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-280.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-120.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-200.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-260.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-230.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-330.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-110.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-320.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-010.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-040.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-310.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-020.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-000.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-200.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-070.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-190.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-110.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-090.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-210.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-290.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-170.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-280.png
/usr/share/icons/gnome/22x22/status/weather-clear-night-120.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-080.png
/usr/share/icons/gnome/22x22/status/weather-few-clouds-night-210.png
/usr/share/icons/gnome/22x22/status/weather-clouds-night.png
/usr/share/icons/HighContrast/scalable/status/weather-clear-night.svg
/usr/share/icons/HighContrast/scalable/status/weather-few-clouds-night.svg
/usr/share/icons/HighContrast/scalable/status/weather-overcast.svg
/usr/share/icons/HighContrast/scalable/status/weather-showers-scattered.svg
/usr/share/icons/HighContrast/scalable/status/weather-few-clouds.svg
/usr/share/icons/HighContrast/scalable/status/weather-showers.svg
/usr/share/icons/HighContrast/scalable/status/weather-severe-alert.svg
/usr/share/icons/HighContrast/scalable/status/weather-fog.svg
/usr/share/icons/HighContrast/scalable/status/weather-storm.svg
/usr/share/icons/HighContrast/scalable/status/weather-clear.svg
/usr/share/icons/HighContrast/scalable/status/weather-snow.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-260.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-260.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-050.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-170.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-000.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-250.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-010.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-090.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-300.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-030.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-040.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-300.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-250.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-100.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-330.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-000.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-070.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-160.svg
/usr/share/icons/Humanity/status/16/weather-clear-night.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-290.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-240.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-320.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-340.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-330.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-070.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-190.svg
/usr/share/icons/Humanity/status/16/weather-overcast.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-060.svg
/usr/share/icons/Humanity/status/16/weather-showers-scattered.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-210.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-270.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-180.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-220.svg
/usr/share/icons/Humanity/status/16/weather-clouds.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-090.svg
/usr/share/icons/Humanity/status/16/weather-clouds-night.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-080.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-350.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-140.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-050.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-240.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-350.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-230.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-310.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-160.svg
/usr/share/icons/Humanity/status/16/weather-showers.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-210.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-280.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-020.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-270.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-040.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-010.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-120.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-020.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-230.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-170.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-030.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-150.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-080.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-280.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-200.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-290.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-320.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-100.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-340.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-310.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-140.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-180.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-120.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-150.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-130.svg
/usr/share/icons/Humanity/status/16/weather-severe-alert.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-200.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-110.svg
/usr/share/icons/Humanity/status/16/weather-fog.svg
/usr/share/icons/Humanity/status/16/weather-storm.svg
/usr/share/icons/Humanity/status/16/weather-few-clouds-night-190.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-130.svg
/usr/share/icons/Humanity/status/16/weather-clear.svg
/usr/share/icons/Humanity/status/16/weather-snow.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-220.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-110.svg
/usr/share/icons/Humanity/status/16/weather-clear-night-060.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-260.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-260.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-050.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-170.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-000.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-250.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-010.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-090.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-300.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-030.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-040.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-300.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-250.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-100.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-330.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-000.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-070.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-160.svg
/usr/share/icons/Humanity/status/48/weather-clear-night.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-290.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-240.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-320.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-340.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-330.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-070.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-190.svg
/usr/share/icons/Humanity/status/48/weather-overcast.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-060.svg
/usr/share/icons/Humanity/status/48/weather-showers-scattered.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-210.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-270.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-180.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-220.svg
/usr/share/icons/Humanity/status/48/weather-clouds.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-090.svg
/usr/share/icons/Humanity/status/48/weather-clouds-night.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-080.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-350.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-140.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-050.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-240.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-350.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-230.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-310.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-160.svg
/usr/share/icons/Humanity/status/48/weather-showers.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-210.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-280.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-020.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-270.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-040.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-010.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-120.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-020.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-230.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-170.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-030.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-150.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-080.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-280.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-200.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-290.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-320.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-100.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-340.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-310.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-140.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-180.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-120.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-150.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-130.svg
/usr/share/icons/Humanity/status/48/weather-severe-alert.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-200.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-110.svg
/usr/share/icons/Humanity/status/48/weather-fog.svg
/usr/share/icons/Humanity/status/48/weather-storm.svg
/usr/share/icons/Humanity/status/48/weather-few-clouds-night-190.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-130.svg
/usr/share/icons/Humanity/status/48/weather-clear.svg
/usr/share/icons/Humanity/status/48/weather-snow.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-220.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-110.svg
/usr/share/icons/Humanity/status/48/weather-clear-night-060.svg
/home/michael/.local/share/Trash/info/weather-indicator-team-ppa-precise.list.trashinfo
/home/michael/.local/share/Trash/info/weather-indicator-team-ppa-precise.2.list.trashinfo

``` 

Go on a limb and say it's because it was Gnome's version that was installed somehow and not Precise's that would cause it to not work properly in the first place. 

I have Synaptic and when I type weather in there's a lot of files that come up (not nearly as much as up there though) but also a lot of files that don't even seem to have anything to do with "weather".

---

### Post by stinkeye on 2013-06-11
> **Bashing-om said:**
> [COLOR=#000000]
And to look at that file that is to be edited:

```
cat /etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list
```
Post that output back for advise on editing the file in the text editor "gedit"
[/COLOR][INDENT][COLOR=#000000]
3 steps forward on 1 back

[/COLOR][/INDENT]


> **Overlooks said:**
> Entering the first code brings this:
```
ls: cannot access /etc/apt/sources/list.d/: No such file or directory
```

entering the second just says this in the terminal:
```
net/weather-indicator-team/ppa/ubuntu precise main #A weather indicator for Ubuntu's Indicator Applet

```

Should not your **/etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list** be of this format 
```
**deb http://ppa.launchpad.**net/weather-indicator-team/ppa/ubuntu precise main #A weather indicator for Ubuntu's Indicator Applet
```
Eg mine for raring...
> [COLOR="#008000"]glen@Raring:~$[/COLOR] cat /etc/apt/sources.list.d/weather-indicator-team-ppa-raring.list
**deb [http://ppa.launchpad](http://ppa.launchpad).**net/weather-indicator-team/ppa/ubuntu raring main
# deb-src [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu) raring main

...and the downloaded package name is **indicator-weather** not weather-indicator

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks; hummm

looks maybe like we may have opened a can of worms, want to make sure they do not become snakes..
Let's look at what the package manager says about the overall state.
```
sudo dpkg -C ## that is a uppercase "c"
[/COLOR]apt-cache policy weather-indicator
dpkg-query -s weather-indicator

```
and I want to make double sure about things...
in the file manager go to /var/lib/dpkg/status
It is a huge file
and look for any stanza for "weather-indicator" and post back that stanza
also post the output:
```

ls -la /var/lib/dpkg/info/weather-indicator

```[INDENT=2]help put out forest fires

[/INDENT]

---

### Post by Overlooks on 2013-06-11
> **stinkeye said:**
> Should not your **/etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list** be of this format 
```
**deb http://ppa.launchpad.**net/weather-indicator-team/ppa/ubuntu precise main #A weather indicator for Ubuntu's Indicator Applet
```
Eg mine for raring...

I might have miss copied the whole line but I think it was missing that. I tried to recreate it but it no longer exists.

> **Bashing-om said:**
> [COLOR=#000000]Overlooks; hummm

looks maybe like we may have opened a can of worms, want to make sure they do not become snakes..
Let's look at what the package manager says about the overall state.
```
sudo dpkg -C ## that is a uppercase "c"

```[/COLOR]```
apt-cache policy weather-indicator
dpkg-query -s weather-indicator

```
and I want to make double sure about things...
in the file manager go to /var/lib/dpkg/status
It is a huge file
and look for any stanza for "weather-indicator" and post back that stanza
also post the output:
```

ls -la /var/lib/dpkg/info/weather-indicator

```[INDENT=2]help put out forest fires

[/INDENT]



First command, nothing happens except it asking for my password and then back to letting me type in commands.

Second one yields this: 
```
N: Unable to locate package weather-indicator
```

and this:
```
Package `weather-indicator' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

I couldn't find a status folder under /dpkg/ so I moved on without it and it gave this when I entered the code:
```
ls: cannot access /var/lib/dpkg/info/weather-indicator: No such file or directory

```

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]@ stinkeye Thanks much !
Trying to identify the package name was driving me nuts... and indicator-weather rings a big bell (now!).

Let us work with the correct package name!
[/COLOR][INDENT=2][COLOR=#000000]
excuse me while I rethink

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]@ Overlooks;
Now that stinkeye has put me onto the right path. try:
[/COLOR]```
sudo ppa-purge ppa:indicator-weather
```

Maybe now all this running a round can cease, and we can get on ![INDENT=2]
big step forward ?

[/INDENT]

---

### Post by Overlooks on 2013-06-11
Nothing: 
```
Warning:  Could not find package list for PPA: ppa:indicator-weather ppa:indicator-weather

```

In an attempt to lighten the mood- at least now I know my "when I break something, I break it good" saying while working on my truck follows me to computers too haha

---

### Post by stinkeye on 2013-06-11
```
sudo ppa-purge ppa:weather-indicator-team/ppa
```
Is what works here.

---

### Post by Overlooks on 2013-06-11
Unfortunately I get the same thing as before, Stinkeye:
```
Updating packages listsPPA to be removed: weather-indicator-team ppa
Warning:  Could not find package list for PPA: weather-indicator-team ppa

```

---

### Post by Bashing-om on 2013-06-11
@ stinkeye ... that one we have run...
and there exist lots of files on the system relating to "weather"... did not want to (re-)install the package from ppa source with residual files from prior installation attempts -> hence my consternation in identification of the source.

About the only thing we can do is to go ahead and install from the ppa ...and live with the results.
[INDENT=2]
are we there yet 
 [/INDENT]

---

### Post by stinkeye on 2013-06-11
> **Overlooks said:**
> Unfortunately I get the same thing as before, Stinkeye:
```
Updating packages listsPPA to be removed: weather-indicator-team ppa
Warning:  Could not find package list for PPA: weather-indicator-team ppa

```
Not really up with what has happened but the ppa has probably been removed
so to purge packages from that ppa you would need to re-add the ppa.
I'll leave it with **Bashing-om** as he has a better idea of what's going on.

---

### Post by Overlooks on 2013-06-11
Alright. Thanks for your help and getting us straightened out. :D

---

### Post by Bashing-om on 2013-06-11
Overlooks;
Looking back I see nothing now to worry about ... 
let's (re-)install !
```
sudo add-apt-repository ppa:weather-indicator-team/ppa
sudo apt-get update
sudo apt-get install indicator-weather

```

See how blind I can be .... there is the package name !

@ stinkeye
Really appreciate the input ... helps bunches !

[INDENT=3]move'n on

[/INDENT]

---

### Post by Overlooks on 2013-06-11
all is good until I enter the last command and it says this: 
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 indicator-weather : Depends: python-pywapi (>= 0.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks; sheesshh,

Ok, see what results:
```
sudo apt-get install python-pywapi
```
[/COLOR]> Description-en: Python wrapper around different weather APIs The module provides a Python wrapper around the Yahoo! Weather, Google Weather
 and National Oceanic and Atmospheric Administration (NOAA) APIs. Fetch weather
 reports using zip code, location id, city name, state, country etc
[INDENT]
still try'n

[/INDENT]

---

### Post by Overlooks on 2013-06-11
Python seems to have installed correctly but when trying to download weather indicator again it says this again: 
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 indicator-weather : Depends: python-pywapi (>= 0.3.2) but 0.2.2-1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks;
This is now a head scratcher... In the repositories is version 0.2.2-1 ... but the package indicator-weather requires version >=0.3.2 ...
In this deep, let me see what I can do about finding it.
[INDENT=2]
I'll be back !

[/INDENT]


[/COLOR]

---

### Post by Bashing-om on 2013-06-11
Overlooks;

Well well well...reported problem to launchpad installing onto precise... and a solution:
```
sudo add-apt-repository ppa:pywapi-devel/ppa
sudo apt-get update
sudo apt-get install python-pywapi

```
[INDENT][INDENT]see how that runs[/INDENT][/INDENT]

---

### Post by Overlooks on 2013-06-11
THANK YOU! it works 100% now.

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]Overlooks; Outstanding !

Now we can get some shut-eye.
I'll lay odds I remember "indicator-weather".
I hope you learned a lot from this experience, but ain't ubuntu wonderful !

Please mark this thread as "solved", it aids others seeking the solution, and helps keep the forum tidy.
[/COLOR]Interim method:> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
All's well that ends well

[/INDENT]

---

### Post by Overlooks on 2013-06-11
Yeah, I learned that I need to read some guides on here so I can be more independent with Ubuntu. haha One day I'll be well versed in it, until then I guess the forum will have to deal with these types of problems that I seem to have a knack for making ;)

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]Overlooks;
No one was born knowing this ! ..It is all a process of learning.

How bout this: Frequent this forum and offer help and advise in an area of interest to you. You will be amazed where the paths will lead you.
[/COLOR][INDENT=3][COLOR=#000000]
howto: feeding your ubuntu[/COLOR][/INDENT]

---

