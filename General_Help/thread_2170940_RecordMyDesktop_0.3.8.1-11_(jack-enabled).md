---
title: "RecordMyDesktop 0.3.8.1-11 (jack-enabled)"
date: 2013-08-28
forum: General Help
---

### Post by omelette on 2013-08-28
**RecordMyDesktop** is something I find really useful.  Unfortunately for years it has proven a real pain to get working properly.  The main problem seems to have involved (working) jack-support.   And if by some miracle Jack started working, another beauty involved Theora-encoding - it just wouldn't work properly!  Luckily I discovered recently that these problems haven't gone unnoticed by some, and patches do exist to fix most of these problems.

Looking for help/source from the official homepage is a no-no - that site hasn't been updated in years.  The latest patches I have been able to find are in a Fedora package, found [here]("http://mirrors.ustc.edu.cn/fedora/fedora/linux/development/rawhide/source/SRPMS/r/recordmydesktop-0.3.8.1-11.fc20.src.rpm").  The latest RecordMyDesktop for Ubuntu 13.04 seems to be **'recordmydesktop_0.3.8.1+svn602-1ubuntu3_i386.deb' **, and although I don't have it installed (still using 10.04, boo!) I have tried running it on **Linux Deepin**, the Chinese Ubuntu 13.04-derived Linux, and where it is also the most current version available in the  repositories - and it doesn't work!!!  Some error about the screen not being recognised, or along those lines.  Thankfully the Fedora-patched version built on my Ubuntu 10.04 setup works perfectly on all 3 of my computers, so it should also work with Ubuntu 13.04 etc.

One other thing. In order to record flash audio from a browser, you need to build the ['libflashsupport-jack']("http://jackaudio.org/routing_flash") browser-plugin.  This works perfectly with both Firefox and Chromium on my setups.  Needless to say, you also need Jack itself installed.  While building 'libflashsupport-jack' on Ubuntu 10.04 was not an issue, I failed to build it on Linux Deepin, despite various attempts at 'tweaking' the source.  As there is no package as such produced at build-time, at least according to 'checkinstall', there is nothing to include here.  I also think there is some controversy surrounding this plugin due to copyright reasons, and the reason it is not included with most/any Linux distribution.  I'd be interested to hear if anyone has managed to build the browser-plugin on the current Ubuntus.

If interested, you may either download the source from the above link, apply the included patches and build it yourself, or you can get my 'checkinstall' builds from the below links.  A big thank-you from me to whoever is responsible for finally fixing this. 
  
[RecordMyDesktop 0.3.8.1-11]("http://ubuntuone.com/6G4d0WPvw1R9dKiYSMNdym")
[Gtk-RecordMyDesktop 0.3.8.1]("http://ubuntuone.com/0WgHcuBt5R3oERALjYlNDi")

---

