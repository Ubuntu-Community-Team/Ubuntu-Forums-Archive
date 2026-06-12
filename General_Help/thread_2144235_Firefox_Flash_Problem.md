---
title: "Firefox Flash Problem"
date: 2013-05-11
forum: General Help
---

### Post by xXSIEGEXx on 2013-05-11
When I open up Firefox and go to a site that uses adobe flash, at the top of the screen I get "Additional plugins are required to display all the media on this page [Install Plugins]". When I click on the Install Plugins I get a pop up saying Firefox is searching for available plugins with a moving bar beneath it. It just does that for hours and I can never get flash installed.

Even terminal wont work for me! Please help!
sudo apt-get install flashplugin-installer:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following package was automatically installed and is no longer required:
kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
libnspr4-0d
Suggested packages:
x-ttcidfont-conf ttf-mscorefonts-installer ttf-bitstream-vera ttf-dejavu
ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
flashplugin-installer libnspr4-0d
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

---

### Post by fantab on 2013-05-11
You get the error because you are perhaps, using two apt-get programs... one is running apt-get in terminal, the other could be software updater or Software center. Only one apt-get utility at a time.

Install 'Synaptic' Package Manager, it is better than Software Center, and makes installing packages easier.

If you still get the above error even after ensuring that only one apt-get utility is running, then:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

To install flash plugin you can install "ubuntu-restricted-extras". It not only installs 'flash' but also has closed source codecs and microsoft fonts. To install microsoft fonts you need to accept their EULA.

sudo apt-get install ubuntu-restricted-extras

---

### Post by xXSIEGEXx on 2013-05-11
The problem is resolved, thank you.

---

### Post by pstree on 2013-05-11
change topic to Solved!

---

