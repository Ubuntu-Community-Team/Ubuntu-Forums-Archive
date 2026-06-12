---
title: "Flash no longer working in Chromium or Firefox"
date: 2014-08-09
forum: General Help
---

### Post by fizikz on 2014-08-09
After a recent system software update, flash no longer works in Chromium (Version 36.0.1985.125 Ubuntu 12.04 (283153)) or Firefox (version 31.0). I followed the instructions [here]("http://askubuntu.com/questions/449103/chromium-34-cant-detect-flash-plugin") to install the pepper flash plugin, but it still doesn't work. If I type "about://plugins" in Chromium, there is still no flash plugin listed. What else can I check?

---

### Post by dave131 on 2014-08-10
Does it no longer work, or are you going to a site that requires an updated version of flash?  Adobe stopped support for Flash for Linux at 11. something.

You could also try:

sudo apt-get install flashplugin-installer

---

### Post by fizikz on 2014-08-10
Maybe both. I visited [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/") to test the installation/version of flash. In Chromium, the spot where a version would show says "This plugin is not supported". In Firefox it shows version 11.2.202.394.

---

### Post by craig10x on 2014-08-10
Install Chrome...it's got the latest flash on the pepperflash plug in and it's already installed by default...rather then struggling to get pepper working on chromium...
Chrome also has a nice built in pdf reader and puts a ppa in software sources on ubuntu so that you get the latest version of it as soon as it arrives, through your software updater...
And they are much newer versions then you get with Chromium....a lot of ADVANTAGES to using the actual Chrome...

---

### Post by fizikz on 2014-08-10
Yes, I did also install Chrome and it works well, but I was hoping to get Firefox and Chromium working too.

---

### Post by vasa1 on 2014-08-10
> **fizikz said:**
> ... What else can I check?
What do you see in the plugins tab of the about:addons page (Alt+T, A) In Firefox?

---

### Post by fizikz on 2014-08-10
> **vasa1 said:**
> What do you see in the plugins tab of the about:addons page (Alt+T, A) In Firefox?

In Firefox, I see exactly the same version and files listed as in your screenshot. In Chromium, no flash plugin is listed (chrome://plugins).

It's possible that some sites require a more recent version of flash (in Firefox), but Chromium is showing no flash plugin at all.

---

### Post by fizikz on 2014-08-10
Well, I got the pepper flash plugin working. I usually have several chromium windows (each with multiple tabs) open. When I installed pepper flash, I restarted chromium by typing "chrome:restart" in the address bar. In the past that was sufficient to apply updates. This time, I manually closed all the windows, and upon restarting, the plugin shows up (version 14.0.0.145). 

As for Firefox, considering the plugin is recognized, I'll assume that it's due to some sites' version requirements that flash might sometimes not work.

---

