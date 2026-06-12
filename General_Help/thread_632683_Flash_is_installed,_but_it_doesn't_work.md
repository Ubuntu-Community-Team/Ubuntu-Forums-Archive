---
title: "Flash is installed, but it doesn't work"
date: 2007-12-05
forum: General Help
---

### Post by crossnore on 2007-12-05
I used synaptic package manager to install flash.  I closed firefox and reopened it and it says flash is not installed.  I typed about:plugins in firefox and it says flash video player is installed and activated.  I also installed libflash-mozilla from synaptic package manager.  Flash sites still do not work.  I am using Edubuntu.  Anyone know what I am doing wrong?  Thanks for your help.

---

### Post by -grubby on 2007-12-05
completely remove anything related to flash in Synaptic and install by visiting a flash site and say if that works

---

### Post by ericartman on 2007-12-05
Or check out 

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

has a little program that I use Ubackup! that has never missed yet for me. (its not just a backup program)

Cart

---

### Post by crossnore on 2007-12-06
awesome, thanks guys, It works now

---

### Post by KayMyst on 2007-12-06
it doesn't work for me guys.
i also tried removing it then installing from adobe's site, but it tells me i need to to remove xpi.dat file
cheers for your help

---

### Post by gitpik on 2007-12-07
I also can not get flash player to work. I tried uninstalling reinstalling and using Ubackup any help would be much appreciated. :)

---

### Post by Spenzer4Hire on 2007-12-07
I, too, am suddenly having flash issues.  Haven't had any problems with flash on Gutsy until yesterday.  3 fresh installs on 3 computers, fully updated..  One 64 bit and 2 32 bit installs.  I've installed through synaptic (Ubuntu restricted extras) and I've installed through the Firefox prompt.  In both cases the package installs but does not show up when I type about:plugins.  I've tried purging any flash related packages and re-installing, but the results are the same.

Any ideas?  Were there any recent updates to the flash plugin that might have broken something?

---

### Post by varanasi on 2007-12-07
The md5 in the install files doesn't match the md5 for the flash file currently available on adobe.  Until someone changes the package's md5, synaptic will appear to install flash and report that it is installed, though flash is not actually installed.  

Check the detailed view in synaptic during the "install."  After the download, the install fails because of an md5 conflict:
> md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
Despite many recommendations to use apt-get in many threads, it's the same deal with apt-get for the same reason.  

There is a suggested work-around [here]("http://ubuntuforums.org/showpost.php?p=3902460&postcount=31").  I haven't tried it yet.  (If you are new, substitute nano for vi if you try to follow the instructions.)

There's another plausible workaround [here]("http://ubuntuforums.org/showpost.php?p=3899129&postcount=4").

There are bug reports [here]("https://bugs.launchpad.net/bugs/174090") and [here]("https://bugs.launchpad.net/bugs/173890").

---

### Post by Spenzer4Hire on 2007-12-07
Thanks a bunch Varanasi.

---

### Post by subSkipper on 2007-12-07
Thanks varanasi, I'll give it a try.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

