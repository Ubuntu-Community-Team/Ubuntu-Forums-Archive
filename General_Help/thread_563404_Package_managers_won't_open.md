---
title: "Package managers won't open"
date: 2007-09-29
forum: General Help
---

### Post by AnarchoVegan on 2007-09-29
Hi Everyone

Last night I left my computer on overnight to upgrade to Gutsy Gibbon, but this morning someone kicked the comp cable and it turned off. 
I turned on my comp, and the updates button appears at the top panel, but when I click it nothing happens.

when i try to go into synaptic package manager, I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I ran "dpkg --configure -a" but nothing happens.

as well as that, desktop effects won't work, and my 'restart' and 'turn off computer' buttons are missing :confused:

How can I restart the upgrade, and fix this problem?

Help would be very much appreciated!

peace,
jimmy

---

### Post by taurus on 2007-09-29
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by g2g591 on 2007-09-29
also try sudo apt-get install -f, it would appear after sudo dpkg--configure -a in that list above

---

### Post by AnarchoVegan on 2007-09-30
jimmy@jimmy-desktop:~$ sudo dpkg --configure -a
Password:
dpkg: status database area is locked by another process
jimmy@jimmy-desktop:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jimmy@jimmy-desktop:~$ sudo apt-get upgrade
]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jimmy@jimmy-desktop:~$ ]


:confused:

---

### Post by taurus on 2007-09-30
Do you happen to have synaptic or adept open?  You cannot run "sudo apt-get blah blah blah" while you still have synaptic window open.  Close it first and run those commands again.

---

### Post by AnarchoVegan on 2007-09-30
jimmy@jimmy-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-fusion-plugins-main (>= 0.5.2+git20070917); however:
  Package compiz-fusion-plugins-main is not installed.
 compiz depends on compiz-fusion-plugins-extra (>= 0.5.2+git20070917); however:
  Package compiz-fusion-plugins-extra is not installed.
 compiz depends on libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2); however:
  Package libcompizconfig0 is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgnomeui-0 (>= 2.19.1); however:
  Version of libgnomeui-0 on system is 2.17.92-0ubuntu1.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnomeui-0 (>= 2.19.1); however:
  Version of libgnomeui-0 on system is 2.17.92-0ubuntu1.
 compiz-gnome depends on libmetacity0 (>= 1:2.19.5); however:
  Version of libmetacity0 on system is 1:2.18.2-0ubuntu1.1.
 compiz-gnome depends on libwnck22 (>= 2.19.5); however:
  Package libwnck22 is not installed.
 compiz-gnome depends on libcompizconfig-backend-gconf; however:
  Package libcompizconfig-backend-gconf is not installed.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz
 update-notifier
 compiz-gnome
jimmy@jimmy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-plugins consolekit fast-user-switch-applet ghostscript ghostscript-x
  gs-common gs-esp gs-esp-x libcompizconfig-backend-gconf libcompizconfig0
  libcupsimage2 libgnomeui-0 libgnomeui-common libgs8 libmetacity0 metacity
  metacity-common python-cups system-config-printer ubuntu-desktop
  xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
Recommended packages:
  libpam-ck-connector psfontmgr hal-cups-utils bluez-gnome bogofilter cups-pdf
  discover1 displayconfig-gtk libdeskbar-tracker libpam-gnome-keyring pidgin
  pxljr splix totem-mozilla tracker-search-tool ttf-indic-fonts-core
  ttf-unfonts-core ubufox xdg-utils xresprobe
The following packages will be REMOVED:
  compiz compiz-gnome desktop-effects
The following NEW packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main consolekit
  fast-user-switch-applet ghostscript ghostscript-x
  libcompizconfig-backend-gconf libcompizconfig0 libgs8 python-cups
  system-config-printer xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
The following packages will be upgraded:
  compiz-core compiz-plugins gs-common gs-esp gs-esp-x libcupsimage2
  libgnomeui-0 libgnomeui-common libmetacity0 metacity metacity-common
  ubuntu-desktop
12 upgraded, 14 newly installed, 3 to remove and 712 not upgraded.
3 not fully installed or removed.
Need to get 3144kB/9144kB of archives.
After unpacking 18.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
jimmy@jimmy-desktop:~$ 
jimmy@jimmy-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-fusion-plugins-main (>= 0.5.2+git20070917); however:
  Package compiz-fusion-plugins-main is not installed.
 compiz depends on compiz-fusion-plugins-extra (>= 0.5.2+git20070917); however:
  Package compiz-fusion-plugins-extra is not installed.
 compiz depends on libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2); however:
  Package libcompizconfig0 is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgnomeui-0 (>= 2.19.1); however:
  Version of libgnomeui-0 on system is 2.17.92-0ubuntu1.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnomeui-0 (>= 2.19.1); however:
  Version of libgnomeui-0 on system is 2.17.92-0ubuntu1.
 compiz-gnome depends on libmetacity0 (>= 1:2.19.5); however:
  Version of libmetacity0 on system is 1:2.18.2-0ubuntu1.1.
 compiz-gnome depends on libwnck22 (>= 2.19.5); however:
  Package libwnck22 is not installed.
 compiz-gnome depends on libcompizconfig-backend-gconf; however:
  Package libcompizconfig-backend-gconf is not installed.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz
 update-notifier
 compiz-gnome
jimmy@jimmy-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-plugins consolekit fast-user-switch-applet ghostscript ghostscript-x
  gs-common gs-esp gs-esp-x libcompizconfig-backend-gconf libcompizconfig0
  libcupsimage2 libgnomeui-0 libgnomeui-common libgs8 libmetacity0 metacity
  metacity-common python-cups system-config-printer ubuntu-desktop
  xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
Recommended packages:
  libpam-ck-connector psfontmgr hal-cups-utils bluez-gnome bogofilter cups-pdf
  discover1 displayconfig-gtk libdeskbar-tracker libpam-gnome-keyring pidgin
  pxljr splix totem-mozilla tracker-search-tool ttf-indic-fonts-core
  ttf-unfonts-core ubufox xdg-utils xresprobe
The following packages will be REMOVED:
  compiz compiz-gnome desktop-effects
The following NEW packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main consolekit
  fast-user-switch-applet ghostscript ghostscript-x
  libcompizconfig-backend-gconf libcompizconfig0 libgs8 python-cups
  system-config-printer xdg-user-dirs xdg-user-dirs-gtk xvnc4viewer
The following packages will be upgraded:
  compiz-core compiz-plugins gs-common gs-esp gs-esp-x libcupsimage2
  libgnomeui-0 libgnomeui-common libmetacity0 metacity metacity-common
  ubuntu-desktop
12 upgraded, 14 newly installed, 3 to remove and 712 not upgraded.
3 not fully installed or removed.
Need to get 3144kB/9144kB of archives.
After unpacking 18.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
jimmy@jimmy-desktop:~$ 


I ran all the commands but this is what it said :(

---

### Post by SpiritIsReality on 2007-09-30
howdy
gotta google the line
dpkg: dependency problems prevent configuration of compiz:
[edit]and the lines with Error . I can't seem to find the right one
Error code exit status 1 (omething like it)[/edit}
we have to go thru the list and write down all the package names it wants.??
buds

---

### Post by metalpancake on 2007-09-30
you can try simply adding 'sudo' to the front of the code it asks you to use.
It worked for me when I had the same problem.

---

### Post by SpiritIsReality on 2007-09-30
howdy
metalpancake ...good to see you .
unfortunately I see a sudo in front .
but that can be the answer quite often, you are right there.

jimmy@jimmy-desktop:~$ sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz depends on libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2); however:
  Package libcompizconfig0 is not installed.

a bunch of packages which compiz depends, but apt will not install them
[quote]
      g2g591              **Re: Package managers won't open**
         also try sudo apt-get install -f, it would appear after sudo dpkg--configure -a in that list above            2 Hours Ago 08:56 PM       taurus              **Re: Package managers won't open**
         Open a terminal and run

Applications -> Accessories -> Terminal
     Code:
     sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade[ /quote]

---

### Post by SpiritIsReality on 2007-09-30
:-k

[http://www.google.ca/search?hl=en&q=E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&btnG=Google+Search&meta=]("http://www.google.ca/search?hl=en&q=E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&btnG=Google+Search&meta=")
buds
[edit]: used wrong search term. Had my wires crossed with another thread. my apologies to all.
 ... taurus ... any ideas what could be getting in the way?, besides me I mean.
........I searched with a better line this time.
........[http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=dpkg+dependency+problems+prevent+configuration&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=dpkg+dependency+problems+prevent+configuration&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
........buds ... anybody got any ideas ?

---

### Post by SpiritIsReality on 2007-09-30
howdy
the app aptitude looks like it will help with apps like compiz
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)
[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
aptitude guides
[http://www.google.ca/search?hl=en&q=linux+aptitude+guides+%28ubuntu+OR+debian%29&btnG=Search&meta=]("http://www.google.ca/search?hl=en&q=linux+aptitude+guides+%28ubuntu+OR+debian%29&btnG=Search&meta=")
buds

edit : [http://www.google.ca/search?hl=en&q=aptitude+howto+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=aptitude+howto+&btnG=Search&meta=)
OK aptitude
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
[http://people.debian.org/~dburrows/aptitude-doc/en/](http://people.debian.org/~dburrows/aptitude-doc/en/)

---

