---
title: "update flash player"
date: 2015-07-03
forum: General Help
---

### Post by rybnik on 2015-07-03
In Firefox, whenever I'm on a webpage that has an embedded video that uses flash, I see [this message]("http://i.imgur.com/BhlAmvC.jpg") covering the playback window.

However, sudo apt-get upgrade does not find any available updates.

If my flash plugin is indeed outdated, then how can I update it, given that apt-get upgrade does not see any available updates?

---

### Post by kerry_s on 2015-07-03
adobe no longer supports linux flash. the version in the repo is the last version available.
[http://m.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html?m=1](http://m.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html?m=1)

---

### Post by Dennis N on 2015-07-03
Adobe still supports flash player 11.2:

From the Adobe Web Page:
> Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux. 

source: [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

As of Fri Jul 3, 2015 The latest version is 11.2.202.468
Recommended action: Just wait for it to arrive in the repositories. Sometimes if you use a mirror, there can be a delay in its availability.

---

### Post by VMC on 2015-07-03
I download the '[.tar.gz]("https://get.adobe.com/flashplayer/")' version. Pull out 'libflashplayer.so' file and put it into '/usr/lib/mozilla/plugins'

---

### Post by rybnik on 2015-07-03
VMC's method seems interesting, but I had already installed Pepper Flash (as per the link kerry_s posted) before I saw VMC's post.

Pepper Flash works fine, though.

However, I found the instructions for installing Pepper Flash (at the page linked to by kerry_s) to be somewhat confusing.  For anyone else who wants to install Pepper Flash, I'll write out my own version of instructions that I think is better:  (below)  I figured out the below through a bunch of tinkering, so hopefully I can make it easier for someone out there.

===================

how to install pepper flash for use on firefox:

(0) Install Chromium. (not chrome)
(1) run these commands:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin

(2) download .deb installer file for google chrome. (not chromium)
(3) Extract the .deb file.  The extraction of the .deb file has a file called libpepflashplayer.so in one of the subdirectories.  (Do a search to find it.)
(4) cp that file (libpepflashplayer.so) into /usr/lib/chromium-browser/plugins/ (probably requires root)
(5) change write permissions on /usr/lib/chromium-browser/plugins/libpepflashplayer.so so that non-root user has read and write permissions.  And make it executable.

---

