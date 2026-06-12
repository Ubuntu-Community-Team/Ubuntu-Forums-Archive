---
title: "Synaptic error, can not update/install new packages"
date: 2008-02-11
forum: General Help
---

### Post by GeigerRulesBig on 2008-02-11
I have not been able to install new packages, or update previously installed packages, even with system update. I have been consistently receiving tthis error in synaptic and system update:
```

 E: /var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb: files list file for package `eog' contains empty filename
```

Thank you in advance for any help.


-Geiger

---

### Post by Rocket2DMn on 2008-02-11
Try
```
sudo rm /var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by GeigerRulesBig on 2008-02-11
```
geiger@Silver-Smashed:~$ sudo rm /var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb
[sudo] password for geiger:
rm: cannot remove `/var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb': No such file or directory
geiger@Silver-Smashed:~$ sudo dpkg --configure -a
geiger@Silver-Smashed:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

It says the file is not there. The same error appears for upgrade and clean.


-Geiger

---

### Post by lhardyl on 2008-02-11
I had a similar problem and a reboot solved it for me.

someone said it may have something to do with trying to install 2 things at once or having apt-get upgrade running at shutdown

so yea, give it a reboot and see if that solves ya prob

---

### Post by Rocket2DMn on 2008-02-11
Please list the contents of your archives directory
```
ls /var/cache/apt/archives
```
Also, to run the apt-get commands, you have to close Synaptic (or any other package manager you have open).  Try again :)

---

### Post by GeigerRulesBig on 2008-02-11
```
geiger@Silver-Smashed:~$ ls /var/cache/apt/archivesls /var/cache/apt/archives
ls: /var/cache/apt/archivesls: No such file or directory
/var/cache/apt/archives:
lock  partial

```

I cleared my archive cache early on, to see if that would work. I restarted again, no luck. Synaptic is now set to delete package info after download.

Ran the apt-get commands again (I thought synaptic was closed before, but I guess it took a while for the process to kill. I checked this time through system monitor) this time the upgrade command gave me the following error:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb (--unpack):
 files list file for package `eog' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So, from what I understand, there is something wrong with the Eye of Gnome package, which is somehow disallowing me from adding/removing any other packages (including reloading the EOG package, it refuses to do that too.)

Thanks for the help.


-Geiger

---

### Post by Rocket2DMn on 2008-02-11
You pasted the ls command twice so it didn't work.
Run
```
sudo rm "/var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb"
sudo rm /var/cache/apt/archives/*
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Please make sure you run those correctly, and post back the results.  Again, make sure other package managers are closed.

---

### Post by GeigerRulesBig on 2008-02-11
Results (all other package managers closed)

```
geiger@Silver-Smashed:~$ sudo rm "/var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb"
[sudo] password for geiger:
geiger@Silver-Smashed:~$ sudo rm /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
geiger@Silver-Smashed:~$ sudo dpkg --configure -a
geiger@Silver-Smashed:~$ sudo apt-get clean

```

apt-get update ran with no problems, so omitting that.

```
geiger@Silver-Smashed:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-gnome-support flashplugin-nonfree kdelibs-data kdelibs4c2a skype-common
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.0MB of archives.
After unpacking 2003kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy-updates/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12.2 [18.2kB]
Get:2 http://packages.medibuntu.org gutsy/non-free skype-common 2.0.0.43-0medibuntu2 [2413kB]
Get:3 http://security.ubuntu.com gutsy-security/main firefox-gnome-support 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 [91.8kB]
Get:4 http://archive.ubuntu.com gutsy-updates/main kdelibs-data 4:3.5.8-0ubuntu3.3 [7295kB]                        
Get:5 http://security.ubuntu.com gutsy-security/main firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 [9189kB]     
Get:6 http://archive.ubuntu.com gutsy-updates/main kdelibs4c2a 4:3.5.8-0ubuntu3.3 [10.0MB]                                                                 
Fetched 29.0MB in 1m3s (456kB/s)                                                                                                                           
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb (--unpack):
 files list file for package `eog' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
geiger@Silver-Smashed:~$ 
```

---

### Post by Rocket2DMn on 2008-02-11
OK, maybe you should try to reinstall eog.  I don't understand how, but it just won't let you upgrade FF...
```
sudo rm /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
sudo apt-get install --reinstall eog
```

---

### Post by GeigerRulesBig on 2008-02-11
```
geiger@Silver-Smashed:~$ sudo rm /var/cache/apt/archives/firefox-gnome-support_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
[sudo] password for geiger:
geiger@Silver-Smashed:~$ sudo apt-get install --reinstall eog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libgnomecupsui1.0-1c2a planner libgsf-gnome-1-114 libpth20 libgoffice-0-common abiword-gnome dia-libs esound gnome-office
  abiword-common seahorse gnumeric-common libexiv2-0 gnome-themes-extras dia-gnome libgmp3c2 gnome-backgrounds libcaptury0 libgoffice-0-4
  libstreamanalyzer0 gnome-core dia-common skype-common gnumeric libgpgme11 libcapseo0 libstreams0 exiv2 dbus-x11 inkscape gnome-cups-manager
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 1128kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy-updates/main eog 2.20.1-0ubuntu1 [1128kB]
Fetched 1128kB in 3s (294kB/s)
(Reading database ... dpkg: error processing /var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb (--unpack):
 files list file for package `eog' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
geiger@Silver-Smashed:~$ 

```

Now it just tells me there are too many errors?


-Geiger

---

### Post by chadeldridge on 2008-02-11
Have you tried to purge EOG and then cleanup your apt?

---

### Post by GeigerRulesBig on 2008-02-11
How exactly would I do that? I have cleared out the apt archive cache.


-Geiger

---

### Post by chadeldridge on 2008-02-11
Well if you are sure that eog is actually causing your issue with the firefox install then just sudo apt-get purge eog then do the apt clean again and try to reinstall FF.

Maybe I am totally missing your issue though,

---

### Post by Rocket2DMn on 2008-02-11
Let's do the autoremove like it said,
```
sudo apt-get autoremove
sudo dpkg --configure -a

```
Then post the output of the list file for eog
```
cat /var/lib/dpkg/info/eog.list
```

---

### Post by GeigerRulesBig on 2008-02-11
```
geiger@Silver-Smashed:~$ sudo apt-get purge eog
[sudo] password for geiger:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libgnomecupsui1.0-1c2a planner libgsf-gnome-1-114
  libpth20 libgoffice-0-common abiword-gnome dia-libs esound abiword-common
  seahorse gnumeric-common libexiv2-0 gnome-themes-extras dia-gnome libgmp3c2
  gnome-backgrounds libcaptury0 libgoffice-0-4 libstreamanalyzer0 dia-common
  skype-common gnumeric libgpgme11 libcapseo0 libstreams0 exiv2 dbus-x11
  inkscape gnome-cups-manager
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  eog* gnome-core* gnome-office* ubuntu-desktop*
0 upgraded, 0 newly installed, 4 to remove and 6 not upgraded.
Need to get 0B of archives.
After unpacking 5411kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing gnome-office (--purge):
 files list file for package `eog' contains empty filename
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
geiger@Silver-Smashed:~$ 

```

My issue is that I cannot install new packages, reinstall old packages, upgrade existing packages, or anything like that. It is not just FireFox that is having the issue, I can not upgrade or install any new packages.


-Geiger

---

### Post by GeigerRulesBig on 2008-02-11
```
geiger@Silver-Smashed:~$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
geiger@Silver-Smashed:~$ sudo dpkg --configure -a
geiger@Silver-Smashed:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libgnomecupsui1.0-1c2a planner libgsf-gnome-1-114
  libpth20 libgoffice-0-common abiword-gnome dia-libs esound gnome-office
  abiword-common seahorse gnumeric-common libexiv2-0 gnome-themes-extras
  dia-gnome libgmp3c2 gnome-backgrounds libcaptury0 libgoffice-0-4
  libstreamanalyzer0 gnome-core dia-common skype-common gnumeric libgpgme11
  libcapseo0 libstreams0 exiv2 dbus-x11 inkscape gnome-cups-manager
The following packages will be REMOVED:
  abiword-common abiword-gnome dbus-x11 dia-common dia-gnome dia-libs esound
  exiv2 gnome-backgrounds gnome-core gnome-cups-manager gnome-office
  gnome-themes-extras gnumeric gnumeric-common inkscape libcapseo0 libcaptury0
  libexiv2-0 libgmp3c2 libgnomecupsui1.0-1c2a libgoffice-0-4
  libgoffice-0-common libgpgme11 libgsf-gnome-1-114 libpth20
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 planner seahorse
  skype-common
0 upgraded, 0 newly installed, 32 to remove and 5 not upgraded.
Need to get 0B of archives.
After unpacking 160MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing gnome-office (--remove):
 files list file for package `eog' contains empty filename
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
geiger@Silver-Smashed:~$ 

```

That worked, not. Output for cat /var/lib/dpkg/info/eog.list:
```

geiger@Silver-Smashed:~$ cat /var/lib/dpkg/info/eog.list
/.
/usr
/usr/bin
/usr/bin/eog
/usr/include
/usr/include/eog-2.20
/usr/include/eog-2.20/eog
/usr/include/eog-2.20/eog/eog-application.h
/usr/include/eog-2.20/eog/eog-debug.h
/usr/include/eog-2.20/eog/eog-window.h
/usr/include/eog-2.20/eog/eog-sidebar.h
/usr/include/eog-2.20/eog/eog-dialog.h
/usr/include/eog-2.20/eog/eog-properties-dialog.h
/usr/include/eog-2.20/eog/eog-message-area.h
/usr/include/eog-2.20/eog/eog-error-message-area.h
/usr/include/eog-2.20/eog/eog-file-chooser.h
/usr/include/eog-2.20/eog/eog-statusbar.h
/usr/include/eog-2.20/eog/eog-thumb-nav.h
/usr/include/eog-2.20/eog/eog-transform.h
/usr/include/eog-2.20/eog/eog-image.h
/usr/include/eog-2.20/eog/eog-image-save-info.h
/usr/include/eog-2.20/eog/eog-scroll-view.h
/usr/include/eog-2.20/eog/eog-thumb-view.h
/usr/include/eog-2.20/eog/eog-list-store.h
/usr/include/eog-2.20/eog/eog-thumbnail.h
/usr/include/eog-2.20/eog/eog-job-queue.h
/usr/include/eog-2.20/eog/eog-jobs.h
/usr/include/eog-2.20/eog/eog-plugin.h
/usr/share
/usr/share/gnome
/usr/share/gnome/help
/usr/share/gnome/help/eog
/usr/share/gnome/help/eog/eu
/usr/share/gnome/help/eog/eu/legal.xml
/usr/share/gnome/help/eog/eu/eog.xml
/usr/share/gnome/help/eog/eu/figures
/usr/share/gnome/help/eog/eu/figures/eog_start_window.png
/usr/share/gnome/help/eog/ja
/usr/share/gnome/help/eog/ja/legal.xml
/usr/share/gnome/help/eog/ja/eog.xml
/usr/share/gnome/help/eog/ja/figures
/usr/share/gnome/help/eog/ja/figures/eog_start_window.png
/usr/share/gnome/help/eog/zh_CN
/usr/share/gnome/help/eog/zh_CN/legal.xml
/usr/share/gnome/help/eog/zh_CN/eog.xml
/usr/share/gnome/help/eog/zh_CN/figures
/usr/share/gnome/help/eog/zh_CN/figures/eog_start_window.png
/usr/share/gnome/help/eog/zh_TW
/usr/share/gnome/help/eog/zh_TW/legal.xml
/usr/share/gnome/help/eog/zh_TW/eog.xml
/usr/share/gnome/help/eog/zh_TW/figures
/usr/share/gnome/help/eog/zh_TW/figures/eog_start_window.png
/usr/share/gnome/help/eog/C
/usr/share/gnome/help/eog/C/legal.xml
/usr/share/gnome/help/eog/C/eog.xml
/usr/share/gnome/help/eog/C/figures
/usr/share/gnome/help/eog/C/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/C/figures/eog_start_window.png
/usr/share/gnome/help/eog/de
/usr/share/gnome/help/eog/de/eog.xml
/usr/share/gnome/help/eog/de/figures
/usr/share/gnome/help/eog/de/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/de/figures/eog_start_window.png
/usr/share/gnome/help/eog/en_GB
/usr/share/gnome/help/eog/en_GB/eog.xml
/usr/share/gnome/help/eog/en_GB/figures
/usr/share/gnome/help/eog/en_GB/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/en_GB/figures/eog_start_window.png
/usr/share/gnome/help/eog/es
/usr/share/gnome/help/eog/es/eog.xml
/usr/share/gnome/help/eog/es/figures
/usr/share/gnome/help/eog/es/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/es/figures/eog_start_window.png
/usr/share/gnome/help/eog/fr
/usr/share/gnome/help/eog/fr/eog.xml
/usr/share/gnome/help/eog/fr/figures
/usr/share/gnome/help/eog/fr/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/fr/figures/eog_start_window.png
/usr/share/gnome/help/eog/it
/usr/share/gnome/help/eog/it/eog.xml
/usr/share/gnome/help/eog/it/figures
/usr/share/gnome/help/eog/it/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/it/figures/eog_start_window.png
/usr/share/gnome/help/eog/ko
/usr/share/gnome/help/eog/ko/eog.xml
/usr/share/gnome/help/eog/ko/figures
/usr/share/gnome/help/eog/ko/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/ko/figures/eog_start_window.png
/usr/share/gnome/help/eog/oc
/usr/share/gnome/help/eog/oc/eog.xml
/usr/share/gnome/help/eog/oc/figures
/usr/share/gnome/help/eog/oc/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/oc/figures/eog_start_window.png
/usr/share/gnome/help/eog/pa
/usr/share/gnome/help/eog/pa/eog.xml
/usr/share/gnome/help/eog/pa/figures
/usr/share/gnome/help/eog/pa/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/pa/figures/eog_start_window.png
/usr/share/gnome/help/eog/pt_BR
/usr/share/gnome/help/eog/pt_BR/eog.xml
/usr/share/gnome/help/eog/pt_BR/figures
/usr/share/gnome/help/eog/pt_BR/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/pt_BR/figures/eog_start_window.png
/usr/share/gnome/help/eog/ru
/usr/share/gnome/help/eog/ru/eog.xml
/usr/share/gnome/help/eog/ru/figures
/usr/share/gnome/help/eog/ru/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/ru/figures/eog_start_window.png
/usr/share/gnome/help/eog/sv
/usr/share/gnome/help/eog/sv/eog.xml
/usr/share/gnome/help/eog/sv/figures
/usr/share/gnome/help/eog/sv/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/sv/figures/eog_start_window.png
/usr/share/gnome/help/eog/uk
/usr/share/gnome/help/eog/uk/eog.xml
/usr/share/gnome/help/eog/uk/figures
/usr/share/gnome/help/eog/uk/figures/eog_save_as_window.png
/usr/share/gnome/help/eog/uk/figures/eog_start_window.png
/usr/share/omf
/usr/share/omf/eog
/usr/share/omf/eog/eog-eu.omf
/usr/share/omf/eog/eog-ja.omf
/usr/share/omf/eog/eog-zh_CN.omf
/usr/share/omf/eog/eog-zh_TW.omf
/usr/share/omf/eog/eog-C.omf
/usr/share/omf/eog/eog-de.omf
/usr/share/omf/eog/eog-en_GB.omf
/usr/share/omf/eog/eog-es.omf
/usr/share/omf/eog/eog-fr.omf
/usr/share/omf/eog/eog-it.omf
/usr/share/omf/eog/eog-ko.omf
/usr/share/omf/eog/eog-oc.omf
/usr/share/omf/eog/eog-pa.omf
/usr/share/omf/eog/eog-pt_BR.omf
/usr/share/omf/eog/eog-ru.omf
/usr/share/omf/eog/eog-sv.omf
/usr/share/omf/eog/eog-uk.omf
/usr/share/eog
/usr/share/eog/pixmaps
/usr/share/eog/pixmaps/thumbnail-frame.png
/usr/share/eog/icons
/usr/share/eog/icons/hicolor
/usr/share/eog/icons/hicolor/16x16
/usr/share/eog/icons/hicolor/16x16/actions
/usr/share/eog/icons/hicolor/16x16/actions/eog-plugin.png
/usr/share/eog/icons/hicolor/16x16/actions/eog-image-collection.png
/usr/share/eog/icons/hicolor/22x22
/usr/share/eog/icons/hicolor/22x22/actions
/usr/share/eog/icons/hicolor/22x22/actions/eog-plugin.png
/usr/share/eog/icons/hicolor/22x22/actions/eog-image-collection.png
/usr/share/eog/icons/hicolor/24x24
/usr/share/eog/icons/hicolor/24x24/actions
/usr/share/eog/icons/hicolor/24x24/actions/eog-image-collection.png
/usr/share/eog/icons/hicolor/32x32
/usr/share/eog/icons/hicolor/32x32/actions
/usr/share/eog/icons/hicolor/32x32/actions/eog-plugin.png
/usr/share/eog/icons/hicolor/32x32/actions/eog-image-collection.png
/usr/share/eog/icons/hicolor/scalable
/usr/share/eog/icons/hicolor/scalable/actions
/usr/share/eog/icons/hicolor/scalable/actions/eog-plugin.svg
/usr/share/eog/icons/hicolor/scalable/actions/eog-image-collection.svg
/usr/share/eog/eog.glade
/usr/share/eog/gtkrc
/usr/share/eog/eog-ui.xml
/usr/share/eog/eog-toolbar.xml
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/eog.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/eog.png
/usr/share/icons/hicolor/24x24
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/24x24/apps/eog.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/eog.png
/usr/share/icons/hicolor/scalable
/usr/share/icons/hicolor/scalable/apps
/usr/share/icons/hicolor/scalable/apps/eog.svg
/usr/share/applications
/usr/share/applications/eog.desktop
/usr/share/doc
/usr/share/doc/eog
/usr/share/doc/eog/README
/usr/share/doc/eog/TODO
/usr/share/doc/eog/AUTHORS
/usr/share/doc/eog/THANKS
/usr/share/doc/eog/copyright
/usr/share/doc/eog/NEWS.Debian.gz
/usr/share/doc/eog/changelog.gz
/usr/share/doc/eog/NEWS.gz
/usr/share/doc/eog/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/eog-image-viewer.1.gz
/usr/share/man/man1/eog.1.gz
/usr/share/man/man1/eog-collection-view.1.gz
/usr/share/menu
/usr/share/menu/eog
/usr/share/pixmaps
/usr/share/pixmaps/gnome-eog.xpm
/usr/share/gconf
/usr/share/gconf/schemas
/usr/share/gconf/schemas/eog.schemas
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/eog.pc
/var
&#65533;A&#65533;&#65533;&#65533;G&#65533;&#65533;zGl&#65533;h+&#65533;b&#65533;C

G&#65533;&#65533;zG

Gx+&#65533;b&#65533;A&#65533;&#65533;G&#65533;&#65533;zG&#65533;&#65533;G +&#65533;b&#65533;A'&#65533;&#65533;G*&#65533;&#65533;G*&#65533;&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;U&#65533;G&#65533;U&#65533;Gx+&#65533;&#65533;c&#65533;C'&#65533;&#65533;G&#1717;&#65533;G&#65533;&#65533;&#65533;Gx+&#65533;&#65533;c&#65533;A(&#65533;&#65533;G&#65533;G&#65533;G&#65533;G&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#1384;G&#65533;&#1384;Gx+&#65533;&#65533;c&#65533;E&&#65533;&#65533;G&#65533;&#65533;zG

x+&#65533;&#65533;c&#65533;E&&#65533;&#65533;G&#65533;&#65533;zG&#65533;&#65533;x+&#65533;&#65533;c&#65533;A(&#65533;&#65533;G&#65533;&#65533;zG&#65533;&#65533;G       x+&#65533;&#65533;c&#65533;A&#65533;G&#65533;G&#65533;&#65533;G&#65533;&#65533;G
x+&#65533;&#65533;c&#65533;C&#65533;G&#65533;G&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;G
x+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#46634;G&#46634;G&#9474;+                                                         «&#710;&#9228;                        ýA     '&#8226;ªGÒ&#8230;GÒ&#8230;G                x+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#65533;zG&#65533;&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;b&#65533;G&#65533;b&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#65533;zG&#65533;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;GZ&#2023;GZ&#2023;Gx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#65533;zGD&#65533;Gx+&#65533;&#65533;c&#65533;E'&#65533;&#65533;G&#1492;&#65533;G&#1492;&#65533;x+&#65533;&#65533;c&#65533;A&#1589;&#65533;G&#65533;&#65533;zG8V{Fx+&#65533;&#65533;c&#65533;G'&#65533;&#65533;G&#65533;{G&#65533;{Gnx+&#65533;&#65533;c&#65533;A'&#65533;&#65533;G&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;Gx+&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;+&#65533;Gq7&#65533;Gq7&#65533;GxXW+YW+ZW+[W+\W+]W+^W+_W+`W+aW+bW+cW+dW+&#65533;&#65533;c&#65533;&#65533;&#65533;q7&#65533;Gq7&#65533;Gq7&#65533;G&#65533;gW+hW+iW+jW+kW+lW+mW+nW+oW+pW+qW+tW+rW+&#65533;&#65533;c&#65533;&#65533;HAq7&#65533;Gq7&#65533;Gq7&#65533;G&#65533;yW+zW+{W+|W+}W+~W+W+&#65533;W+&#65533;W+&#65533;W+&#65533;W+&#65533;W+&#65533;W+&#65533;&#65533;c&#65533;&#65533;&#260;U&#65533;Y&#65533;Gp7&#65533;Gp7&#65533;G&#65533;*P+P+

```

---

### Post by Rocket2DMn on 2008-02-11
OK, at least we're making progress now, something clearly got messed up with that file
```
sudo mv /var/lib/dpkg/info/eog.list /var/lib/dpkg/info/eog.list.bak
sudo dpkg --configure -a
sudo apt-get remove --purge eog
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install eog
```

---

### Post by GeigerRulesBig on 2008-02-11
I think that last bit of code did it. EOG was succsefully purged and everything upgraded and installed normally.

Thanks a lot for all the help.


-Geiger

---

### Post by CrazyTycoon on 2008-04-30
thanks...this solved my problem as well with the current update hanging constantly!

---

