---
title: "Flash Updated, Twitter Videos Won't Play In Opera"
date: 2017-12-13
forum: General Help
---

### Post by sasafrass452 on 2017-12-13
Not sure what's going on here, but I just updated adobe flash & once again, twitter videos won't play in Opera. Previously, an update to Opera fixed the issue. Not sure why this is happening again. Is Opera going to be updated again soon? Maybe that'll fix it again? Any help is appreciated!

---

### Post by DuckHook on 2017-12-13
What version and flavour of 'buntu are you running? I don't use Opera, so can't comment on your problem specifically, but it seems to me that if waiting for an Opera update fixed the issue last time, then you may have to do so again. I am guessing that sometimes, the updates between the browser and flash are not in sync.

FWIW, that's why I use FF and Chrome. FF as my main browser precisely because it does *not* have flash (I consider flash to be an inexcusable and gaping security hole) and Chrome because it has Google's version of flash built in for those occasions that I simply must have flash (mainly idiotic government sites that are idiotic because they really shouldn't be using flash).

---

### Post by sasafrass452 on 2017-12-14
I'm using Ubuntu 17.10

> **DuckHook said:**
> What version and flavour of 'buntu are you running? I don't use Opera, so can't comment on your problem specifically, but it seems to me that if waiting for an Opera update fixed the issue last time, then you may have to do so again. I am guessing that sometimes, the updates between the browser and flash are not in sync.

FWIW, that's why I use FF and Chrome. FF as my main browser precisely because it does *not* have flash (I consider flash to be an inexcusable and gaping security hole) and Chrome because it has Google's version of flash built in for those occasions that I simply must have flash (mainly idiotic government sites that are idiotic because they really shouldn't be using flash).

---

### Post by Frogs Hair on 2017-12-14
I don't seem to be having the same problem using the adobe-flashplugin package. I'm using Opera's adblocker though some adblockers block video players as well. Also check the allow flash section in settings.

---

### Post by JamButty on 2017-12-14
I've had the same problem for about a week now. Adblocker on, but this has not stopped video before. Flash is not blocked in settings. YouTube will play, but I understand they convert everything to HTML5. I am not sure this is only flash related as Vimeo, which certainly does not use flash, does not run either. More likely some central problem with Opera and videos. Have to do all video viewing in Chrome. 
First, this result is puzzling.> max@max-inspiron-3847:~$ apt show adobe-flashpluginPackage: adobe-flashplugin
State: not a real package (virtual)
N: Can't select candidate version from package adobe-flashplugin as it has no candidate
N: Can't select versions from package 'adobe-flashplugin' as it is purely virtual
N: No packages found

Then if I used Adobe's version checker ([https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html)), it tells me I do not have adobe installed at all.
Flash does not show up for me in Software Center listings.
If I try to download from Adobe itself (currently offered version 28), I get the error "unknown channel 'artful-partner'

Wassup?

---

### Post by DuckHook on 2017-12-15
> **JamButty said:**
> …this result is puzzling…
*adobe-flashplugin* is not actually a true app. Though it is notionally called a package, it is really just a wrapper for a script that downloads the actual plugin from off site. The plugin is not resident in Ubuntu's repos. This is why flash always updates and downloads separately—it must be pulled directly from Adobe's site (the delights of proprietary software).

Hence, when you do an *apt show*, it tells you that it can't query the repo database to give you any info on this package because the package is not linked to an actual app ("no candidate"). The message you are seeing is only what is to be expected.

---

### Post by JamButty on 2017-12-15
This is frustrating. Flash is there for Chrome, pre-installed. It is not there for Firefox nor for Opera. At least that is what Adobe says.  Since I must have had it previously, it is hard to understand how it suddenly vanished a week ago.  I have tried to install from from the Adobe site APT, Tar.gz and rpm files and could not get any of them to work.

---

### Post by vasa1 on 2017-12-15
Have you tried```
sudo apt-get install flashplugin-installer
```and taking things from there? I guess you'll need to have *xubuntu-restricted-extras* present.

---

### Post by JamButty on 2017-12-15
Will try. I thought as proprietary software, I had to get it directly from Adobe.

---

### Post by JamButty on 2017-12-15
tried the following
> [COLOR=#111111][FONT=Consolas]sudo apt-get install ubuntu-restricted-extras
[/FONT][/COLOR]sudo apt-get install flashplugin-installer
sudo apt-get update

on update got the following hits
> Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security InReleaseHit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful InRelease                     
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-updates InRelease             
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful-backports InRelease           
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:8 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                      



so something for Opera, nothing for Flash. Adobe's checker now recognizes I have some kind of Flash, but can't determine the release. Situation with video using Opera remains unchanged.

---

### Post by again? on 2017-12-15
> **JamButty said:**
> I've had the same problem for about a week now. Adblocker on, but this has not stopped video before. Flash is not blocked in settings. YouTube will play, but I understand they convert everything to HTML5. I am not sure this is only flash related as Vimeo, which certainly does not use flash, does not run either. More likely some central problem with Opera and videos. Have to do all video viewing in Chrome. 
First, this result is puzzling.
```
max@max-inspiron-3847:~$ apt show adobe-flashplugin
Package: adobe-flashplugin
State: not a real package (virtual)
N: Can't select candidate version from package adobe-flashplugin as it has no candidate
N: Can't select versions from package 'adobe-flashplugin' as it is purely virtual
N: No packages found
```
Then if I used Adobe's version checker ([https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html)), it tells me I do not have adobe installed at all.
Flash does not show up for me in Software Center listings.
If I try to download from Adobe itself (currently offered version 28), I get the error "unknown channel 'artful-partner'

Wassup?

This says to me, flash is not installed and the partner repository is not enabled.
When you attempt to download flash from adobe, choosing "Apt for debian", it uses apturl to send a commandline to download flash using your Partner repo.
If not enabled you get the error "unknown channel".
It's the same as running "sudo apt install adobe-flashplugin"

Open software and updates and enable the partner repository.
```
software-properties-gtk --open-tab 1
```
[ATTACH=CONFIG]277852[/ATTACH]

If you don't have a "Canonical Partners" entry you can add via terminal...
```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```

Reload your sources and install flash.
```
sudo apt update
sudo apt install adobe-flashplugin
```

Now check for flash...
```
apt show adobe-flashplugin
```
```
**[COLOR="#008000"]glen@arty:~$[/COLOR] apt show adobe-flashplugin**
Package: adobe-flashplugin
Version: 1:20171212.1-0ubuntu0.17.10.1
Status: install ok installed
Priority: optional
Section: partner/web
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Installed-Size: 35.4 MB
Provides: flashplugin-nonfree
Depends: wget, fontconfig, libc6 (>= 2.11), libfontconfig1 (>= 2.11.94), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:3.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.22.0), libgtk2.0-0 (>= 2.24.31), libnspr4 (>= 2:4.9-2~), libnss3 (>= 2:3.13.4-2~), libpango-1.0-0 (>= 1.14.0), libstdc++6 (>= 4.3), libx11-6, libxt6
Recommends: adobe-flash-properties-gtk (= 1:20171212.1-0ubuntu0.17.10.1) | adobe-flash-properties-kde (= 1:20171212.1-0ubuntu0.17.10.1)
Suggests: firefox | chromium-browser, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5), libnspr4-0d, libnss3-1d
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-downloader, flashplugin-installer, xfs (<< 1:1.0.1-5)
Replaces: flashplugin (<< 6)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash Plugin (http://www.adobe.com)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Plugin
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: Adobe Flash Player plugin
 Adobe® Flash® Player is a cross-platform, browser-based application runtime
 that provides uncompromised viewing of expressive applications, content, and
 videos across browsers and operating systems.
 .
 This package provides plugins compatible with both Chromium and Mozilla based
 web browsers
```

---

### Post by JamButty on 2017-12-15
Thanks guber2!
That's got it mostly done. Up on version 27 now. Firefox now performs correctly. Opera is still screwed and direct downloads from Adobe don't work, but I can live with that. Opera has some nice built-in features that others don't, but it is just too buggy. Coming home to Firefox.

---

### Post by again? on 2017-12-15
> **JamButty said:**
> Thanks guber2!
That's got it mostly done. Up on version 27 now. Firefox now performs correctly. Opera is still screwed and direct downloads from Adobe don't work, but I can live with that. Opera has some nice built-in features that others don't, but it is just too buggy. Coming home to Firefox.
Try [Vivaldi]("https://vivaldi.com"). (built by the original Opera developer)
The main reason I use is because it allows tab interaction, most importantly the ability to click on an open tab to minimize and show previously opened tab.
Based on chromium, like Opera, but with more customisation.
Have been using a while now with no major problems.

---

