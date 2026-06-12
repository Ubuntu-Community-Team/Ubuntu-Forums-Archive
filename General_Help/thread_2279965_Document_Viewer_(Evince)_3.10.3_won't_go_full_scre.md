---
title: "Document Viewer (Evince) 3.10.3 won't go full screen"
date: 2015-05-27
forum: General Help
---

### Post by Ralph L on 2015-05-27
I am installing xubuntu 14.04 and discovered the Document Viewer (Evince) 3.10.3 will no longer go into a real full screen mode like it did in my ubuntu 12.04 system (at least I can't figure out how to do it).  Instead when I select full screen, it still has a menu bar and a toolbar.  I run on a small screen laptop and I really need to have a full screen to display an 8 1/2 by 11 page.  I can't be missing an inch at the top for menus and toolbars.  
Anybody know how to get Evince 3.10.3 to really go full screen????  Anybody know if a newer version would really go full screen, and if so how to install that newer version.  If there isn't a newer version that works, would somebody instruct me on how to install the older version from 12.04 that worked???

Thanks a lot...

---

### Post by ajgreeny on 2015-05-27
Try F11 for what evince calls "Fullscreen" or perhaps F5 for "Presentation" mode which is "real" fullscreen.

PS: I'm on Xubuntu 14.04 but it is still evince 3.10.3

---

### Post by Ralph L on 2015-05-27
ajgreeny.  Thanks for responding, but I don't understand your response.  Evince 3.10.3 (that you mention) is the version that won't go full screen by pressing f11.  On my system there is still a menu bar and a toolbar.  Yes, f5 does go full screen, but I can't use ctrl+ and ctrl- to expand and contract picture.  I use that a lot.  With your system, can you get a REAL full screen by pressing f11.  If so, what are your settings???  I can't make this work.  If there is no way to get Evince 3.10.3 to go to real full screen, would you please give me advice on how I can install the ubuntu 12.04 version in xubuntu 14.04????

---

### Post by ajgreeny on 2015-05-28
No, you are correct and there is still a menubar showing in the F11 fullscreen of evince which is why I wondered if F5 was more like what you want.

Qpdfview is just like evince in thisand retains its menubar, but okular, the KDE pdf viewer goes to a proper fullscreen, so may be worth trying for whatever you want it for.

---

### Post by Ralph L on 2015-05-28
With some difficulty I installed the old version of Evince (Evince 3.4.0) from [http://packages.ubuntu.com/precise-updates/all/](http://packages.ubuntu.com/precise-updates/all/).  I used synaptic to uninstall evince 3.10 that came with xubuntu 14.04.  Then I downloaded from the web site above evince 3.4.0 and tried to install it resulting in several errors ```
ralph@lat1:~$ cd Downloads
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
Selecting previously unselected package evince.
(Reading database ... 183259 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) ...
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.8); however:
  Package libevince3-3 is not installed.
 evince depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not installed.
 evince depends on evince-common (<< 3.5); however:
  Version of evince-common on system is 3.10.3-0ubuntu10.2.
```
I was able to install some of this with synaptic, but each item had several dependencies, some of which weren't in the current repositories.  These I downloaded from the web site above where possible.  If the item wasn't in the precise-updates, I went back to the precise (12.04LTS) original release.  I also used synaptic to uninstall evince-common and then reinstalled the older version (using ralph@lat1:~/Downloads$ sudo dpkg -i evince-common_3.4.0-0ubuntu1.8_all.deb).  Finally after several iterations evince 3.4.0 installed completely.  It seems to work, but I have tested it on only one pdf file.  I was able to remove the toolbar using the view menu and now F11 REALLY is full screen.  I picked evince 3.4.0 for the reinstall, because I knew it worked in ubuntu 12.04.  There may be newer versions of evince that still have a real full screen feature.
Here is the output from Terminal doing the install.  However, remember that in several cases I installed or un-installed things with synaptic between Terminal commands.  Also, I have no idea how badly i screwed up my repositories.
```
ralph@lat1:~$ 
ralph@lat1:~$ 
ralph@lat1:~$ cd Downloads
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
Selecting previously unselected package evince.
(Reading database ... 183259 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) ...
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.8); however:
  Package libevince3-3 is not installed.
 evince depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not installed.
 evince depends on evince-common (<< 3.5); however:
  Version of evince-common on system is 3.10.3-0ubuntu10.2.

dpkg: error processing package evince (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evince
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
Selecting previously unselected package evince.
(Reading database ... 180509 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) ...
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.8); however:
  Package libevince3-3 is not installed.
 evince depends on evince-common (>= 3.4); however:
  Package evince-common is not installed.
 evince depends on evince-common (<< 3.5); however:
  Package evince-common is not installed.

dpkg: error processing package evince (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evince
ralph@lat1:~/Downloads$ sudo dpkg -i libkpathsea5_2009-11ubuntu2_i386.deb
Selecting previously unselected package libkpathsea5.
(Reading database ... 183310 files and directories currently installed.)
Preparing to unpack libkpathsea5_2009-11ubuntu2_i386.deb ...
Unpacking libkpathsea5 (2009-11ubuntu2) ...
Setting up libkpathsea5 (2009-11ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
dpkg: warning: downgrading evince from 3.10.3-0ubuntu10.2 to 3.4.0-0ubuntu1.8
(Reading database ... 183315 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) over (3.10.3-0ubuntu10.2) ...
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.8); however:
  Package libevince3-3 is not installed.
 evince depends on evince-common (<< 3.5); however:
  Version of evince-common on system is 3.10.3-0ubuntu10.2.

dpkg: error processing package evince (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support (3.54ubuntu1.1) ...
Errors were encountered while processing:
 evince
ralph@lat1:~/Downloads$ sudo dpkg -i evince-common_3.4.0-0ubuntu1.8_all.deb
dpkg: warning: downgrading evince-common from 3.10.3-0ubuntu10.2 to 3.4.0-0ubuntu1.8
(Reading database ... 183314 files and directories currently installed.)
Preparing to unpack evince-common_3.4.0-0ubuntu1.8_all.deb ...
Unpacking evince-common (3.4.0-0ubuntu1.8) over (3.10.3-0ubuntu10.2) ...
Setting up evince-common (3.4.0-0ubuntu1.8) ...
Installing new version of config file /etc/apparmor.d/usr.bin.evince ...
Installing new version of config file /etc/apparmor.d/abstractions/evince ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
(Reading database ... 182999 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) over (3.4.0-0ubuntu1.8) ...
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.8); however:
  Package libevince3-3 is not installed.

dpkg: error processing package evince (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evince
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
dpkg: error: dpkg status database is locked by another process
ralph@lat1:~/Downloads$ sudo dpkg -i evince_3.4.0-0ubuntu1.8_i386.deb
(Reading database ... 182989 files and directories currently installed.)
Preparing to unpack evince_3.4.0-0ubuntu1.8_i386.deb ...
Unpacking evince (3.4.0-0ubuntu1.8) over (3.4.0-0ubuntu1.8) ...
Setting up evince (3.4.0-0ubuntu1.8) ...

```

---

### Post by ajgreeny on 2015-05-30
Seems to me it would have been easier and quicker to use okular and just accept the kde and qt dependencies it needs, most of which I have anyway for digikam, the photo manager I prefer, and kmymoney, the finance and bank account manager that I use.

---

