---
title: "Flash issue in Chromium"
date: 2016-11-03
forum: General Help
---

### Post by vertiginous on 2016-11-03
I'm attempting to view the following site in Chromium (version 53.0.2785.143):
[http://pointsoflight.adobeconnect.com/p8s8k8f9xeg/](http://pointsoflight.adobeconnect.com/p8s8k8f9xeg/)

I get redirected to a web page saying: "Adobe Connect requires the Flash Player plugin, version 11.2 or above. Please download and install the Flash Player to continue."



Checking the Ubuntu Software Center, I do have the Adobe Flash plugin installed (version 11.2.202.643ubuntu0.14.04.1).

I've tried installing the Pepper Flash Player browser plugin (version 1.3ubuntu1) too, but I still get the same message when I try to access the site.



I've also tried going to Adobe's Flash Player Help site ([https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html)). When I click "Check Now" to see if Flash is installed, I get the message: "Flash Player is pre-installed in Google Chrome, but not enabled. You can skip the steps below. See Enable Flash Player on Google Chrome."

Following the instructions from the resulting link ([https://helpx.adobe.com/flash-player/kb/enabling-flash-player-chrome.html](https://helpx.adobe.com/flash-player/kb/enabling-flash-player-chrome.html)), I go to chrome://plugins, but there's nothing about Flash listed there. (Only one plugin is listed, for Chromium PDF Viewer.)



What am I missing here?


I'm running Ubuntu 14.04 32-bit.

---

### Post by vertiginous on 2016-11-04
After trying out a couple other things, the instructions from the following page have gotten the original site working:
[https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash)

Basically, going into the Ubuntu Software Center, adding the Canonical Partners software source, and then searching for adobe-flashplugin and installing.



(I went back and double-checked Adobe's Flash Player Help site, and also chrome://plugins, after completing the steps above. Both now recognize that Flash is installed, which was reassuring for a relative novice like myself: as diagnostics, they weren't mistaken when I first tried them.)

---

