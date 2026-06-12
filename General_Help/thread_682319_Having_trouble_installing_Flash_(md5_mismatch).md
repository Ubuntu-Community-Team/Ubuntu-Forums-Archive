---
title: "Having trouble installing Flash (md5 mismatch)"
date: 2008-01-29
forum: General Help
---

### Post by webdude on 2008-01-29
I just installed ubuntu 7.10 on an extra pc, I installed it because I've been running FreeBSD for about   10 years already and never had these kind of problems with installing applications and since I heard so much about ubuntu and their package managers (freebsd has this for quite a while, it already had it when I first installed it about 10 years.  I've been trying to install flashplugin-nonfree so it can make by web browsing a little more pleasant and I've tried with synaptic and with prompt running the apt-get install command to no avail. All I get is this:

22:23:39 (479.21 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I can't understand how come I'm getting a mismatch on md5sum if it's downloading from direct from adobe.  Tried to install i manually by running their script but when it asks me for destination directory I type the correct directory to the mozilla plugins and it comes back to enter a valid directory.

Does anyone have any idea as to why this is happenning.

Best regards,
Eddie

---

### Post by jrusso2 on 2008-01-29
When all else fails copy and paste the two files into your plugins directory.

---

### Post by PeterJS on 2008-01-29
It's a know bug, something to do with release schedules, there's a support thread about it over here:
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by steveneddy on 2008-01-29
I thought flash was in the repos.

---

### Post by webdude on 2008-01-29
what two files?

---

### Post by PeterJS on 2008-01-29
> **steveneddy said:**
> I thought flash was in the repos.

It is, it's just broken right now. The way the package works is that it downloads the installer from adobe, runs it with a known set of inputs, and the records package meta data corresponding to files the installer should have created. But since adobe has changed the installer it's md5 no longer matches when downloaded, hence the above error.

---

### Post by kernelCompile on 2008-01-30
The flash plugin package for Gutsy is broken. If you download the tarball from the Adobe Flash site and follow the installation instructions there Flash will work . Doing this, however, means that the package manager does not know about the Flash plugin (no automatic updates)..

---

### Post by PeterJS on 2008-01-30
> **kernelCompile said:**
> The flash plugin package for Gutsy is broken. If you download the tarball from the Adobe Flash site and follow the installation instructions there Flash will work . Doing this, however, means that the package manager does not know about the Flash plugin (no automatic updates)..

I just learned that you can run the adobe installer with checkinstall, it won't upgrade cleanly, but it will make removing it a whole lot easier so you can upgrade cleanly down the line.
```

sudo checkinstall ./flashplayer-install

```

---

### Post by stchman on 2008-01-30
> **webdude said:**
> I just installed ubuntu 7.10 on an extra pc, I installed it because I've been running FreeBSD for about   10 years already and never had these kind of problems with installing applications and since I heard so much about ubuntu and their package managers (freebsd has this for quite a while, it already had it when I first installed it about 10 years.  I've been trying to install flashplugin-nonfree so it can make by web browsing a little more pleasant and I've tried with synaptic and with prompt running the apt-get install command to no avail. All I get is this:

22:23:39 (479.21 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I can't understand how come I'm getting a mismatch on md5sum if it's downloading from direct from adobe.  Tried to install i manually by running their script but when it asks me for destination directory I type the correct directory to the mozilla plugins and it comes back to enter a valid directory.

Does anyone have any idea as to why this is happenning.

Best regards,
Eddie

If you need Flash 9 then do the following:

```
sudo apt-get -y install flashplugin-nonfree
```

This assumes you are running Feisty or later.  Flash 9 is in the Edgy backports.

What could be simpler?

---

### Post by Motorhead Kaze on 2008-01-31
Hello.

Give up on Ubuntu and go where?  Nobody loves ya like Ubuntu! This week has been interesting for me as well.  K3b went AWOL and Flashplayer blew a fuse.  BUT things get fixed soon around here, so I wouldn't just call it quits with Ubuntu, especially since, as you said Webdude, you just installed it.  Proof:  After about 3-4 days of no K3b, it's back again.  Lots of people in the forums helped me fix it. 

I have used the install from Adobe, sudo checkinstall ./flashplayer-install, sudo apt-get -y install flashplugin-nonfree **AND** the bug fix at [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) these were all very simple to execute, but none of which made Flashplayer 9 work for me.  I'm using the most recent Firefox (fresh today!) in very fresh (reformatted the disc last week) Gutsy.

The thing is broken.  And none of the above are working, at least in my computer.  The bug fix on the link above says not to do sudo apt-get -y install flashplugin-nonfree, but rather, if you have it, to delete it and use the fix, but that didn't work for me.  

Are these things you all actually tried, after experiencing a buggy Flashplayer?  I am open to another suggestion.  This is the only drawback to upgrading every 6 months, sometimes programs (Kdenlive) don't keep up.

P.S. JRusso2, please point us directly to these 2 files, by way of explaining where the plugins directory is.  I myself still don't know what I'm looking at in the files in the filesystem.  I'll try that next.

---

### Post by Knot_Sharpe on 2008-02-01
> **Motorhead Kaze said:**
> Hello.

Give up on Ubuntu and go where?  Nobody loves ya like Ubuntu! This week has been interesting for me as well.  K3b went AWOL and Flashplayer blew a fuse.  BUT things get fixed soon around here, so I wouldn't just call it quits with Ubuntu, especially since, as you said Webdude, you just installed it.  Proof:  After about 3-4 days of no K3b, it's back again.  Lots of people in the forums helped me fix it. 

I have used the install from Adobe, sudo checkinstall ./flashplayer-install, sudo apt-get -y install flashplugin-nonfree **AND** the bug fix at [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) these were all very simple to execute, but none of which made Flashplayer 9 work for me.  I'm using the most recent Firefox (fresh today!) in very fresh (reformatted the disc last week) Gutsy.

The thing is broken.  And none of the above are working, at least in my computer.  The bug fix on the link above says not to do sudo apt-get -y install flashplugin-nonfree, but rather, if you have it, to delete it and use the fix, but that didn't work for me.  

Are these things you all actually tried, after experiencing a buggy Flashplayer?  I am open to another suggestion.  This is the only drawback to upgrading every 6 months, sometimes programs (Kdenlive) don't keep up.

P.S. JRusso2, please point us directly to these 2 files, by way of explaining where the plugins directory is.  I myself still don't know what I'm looking at in the files in the filesystem.  I'll try that next.

I have tried most of this myself, too and have gotten nowhere over a number of days and more than 10 hours of screwing around.  Many  posters refer to an endless loop of same-ole suggestions that are NOT working.  Viewing flash content is pretty basic to the browsing experience ... should it be broken for this long?  Last fix I tried wouldn't take because the installer says I have a newer version (which of course I can't find since I've tried so many peoples suggestions, fixes, additions, deletions, etc.).

End of rant.  Any help gratefully accepted, nothing fancy here.  Extra P4 box, 7.1 with nice CompizFusion windows and 3D cubes, wireless net, just want to watch a little Utube .... Please???

Thanks for any suggestions in advance.
Gary

---

### Post by GreenMeanie on 2008-02-01
You can just goto somewhere like youtube and when the popup shows up install flash from adobe.

I heard they are not putting flash in the next version anyways from Debian.

---

### Post by jeffus_il on 2008-02-01
Here is a site which gives you the flash player as a .deb debian package. Download and open it by default with gdebi, then hit the install button, That's all.
[http://www.bubub.org/blog/ubuntu-flash-9-plugin-not-install-problems/](http://www.bubub.org/blog/ubuntu-flash-9-plugin-not-install-problems/)

---

### Post by aysiu on 2008-02-01
I've changed the title of this thread to more accurately reflect the support request at hand.

---

### Post by laney on 2008-02-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fixes for this have been released to *-proposed as of today. If you enable these in Synaptic, flash should install correctly. Providing the updates prove to work well, they should move to -updates in a few days, becoming part of the official stable version.

---

### Post by wolfen69 on 2008-02-01
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by DouglasAWh on 2008-03-13
> **stchman said:**
> If you need Flash 9 then do the following:

```
sudo apt-get -y install flashplugin-nonfree
```

This assumes you are running Feisty or later.  Flash 9 is in the Edgy backports.

What could be simpler?

If only it worked....

---

### Post by DouglasAWh on 2008-03-13
should this be marked solved?  wolfen's suggestion worked for me.  Strange it seems, since I tried to roll my own .deb using alien, but apparently I did something wrong...

---

