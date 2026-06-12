---
title: "Evince upgrade problem...HELP!"
date: 2006-12-07
forum: General Help
---

### Post by goldenatom on 2006-12-07
An update stalled last night (computer just froze up) and something called evince didn't finish installing. I tried to do a -f install, didn't work though. I tried to remove it, with the thought of reinstalling it...but this is what I get...

```
joe@joe-desktop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evince
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4207kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116079 files and directories currently installed.)
Removing evince ...
Segmentation fault (core dumped)
dpkg: error processing evince (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 evince

```

---

### Post by goldenatom on 2006-12-07
Here is some more-
```
joe@joe-desktop:~$ sudo apt-get install evince
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evince is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0B/902kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package evince.
(Reading database ... 116080 files and directories currently installed.)
Preparing to replace evince 0.6.1-0ubuntu1.2 (using .../evince_0.6.1-0ubuntu1.2_i386.deb) ...
Unpacking replacement evince ...
Setting up evince (0.6.1-0ubuntu1.2) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 evince
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by goldenatom on 2006-12-07
I figured out evince has something to do with the desktop...right? Well I tried to install ubuntu desktop again and got this...

```
joe@joe-desktop:~$ sudo apt-get install ubuntudesktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntudesktop
joe@joe-desktop:~$ sudo apt-get install ubuntu desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu
joe@joe-desktop:~$ sudo apt-get isntall ubuntu-desktop
E: Invalid operation isntall
joe@joe-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntu-desktop
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 17.0kB of archives.
After unpacking 45.1kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com edgy/main ubuntu-desktop 1.30 [17.0kB]
Fetched 17.0kB in 2s (7101B/s)         
Selecting previously deselected package ubuntu-desktop.
(Reading database ... 116172 files and directories currently installed.)
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.30_i386.deb) ...
Setting up evince (0.6.1-0ubuntu1.2) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evince
 ubuntu-desktop
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tomcat1965 on 2006-12-07
You could try --purge remove evince and re-install it.Evince is a document viewer that can read pdf's.
If it wont install correctly you could use Adobe Reader from synaptic,though personally think evince works really well especially for displaying pdf's in presentation mode like online magazines.

---

### Post by goldenatom on 2006-12-07
Tried that and got this 

```
joe@joe-desktop:~$ sudo apt-get --purge remove evince
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntu-desktop evince
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evince* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4252kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116174 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing evince ...
Segmentation fault (core dumped)
dpkg: error processing evince (--purge):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 evince
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Even though its only used to view PDFs, my system seems really "messed up." None of the icons in Applications, Places, or System show up anymore. My windows don't minimize. THe trash bin became an icon on the desktop...just lots of weird things.

---

### Post by goldenatom on 2006-12-07
Any other ideas out there? I'd really rather not reinstall over something like this.

---

### Post by dakap on 2006-12-08
Hi,

try the following commands in a terminal:

sudo apt-get update

after wich you'll probarbly get an error message at the end and then enter:

sudo dpkg --configure -a

..and give it some time.
That did the trick for me ;-)

Good luck!

---

### Post by kidcharles on 2007-01-21
I had the same problem, the update hang for a very long time (10-15 minutes) on evince, but eventually finished without errors.

---

