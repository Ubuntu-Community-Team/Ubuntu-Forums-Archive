---
title: "HPLIP problem, no text, just graphics HP DeskJet 932C"
date: 2007-12-04
forum: General Help
---

### Post by Pierre Fortier on 2007-12-04
I did a new install of Ubuntu 7.10, no problems, no errors. I loaded the HPLIP package, ran the toolbox, setup new device, it saw an HP Deskjet 930C. I followed it's driver selection to an HP Deskjet 932C driver, and completed the install, and printed a test page. The page printed all of the graphics, the picture, the box around the page, the lower boxes, and the HP logo at the bottom, but no text at all on the page - no title, no text in the boxes, nothing.

I tried printing a text file, the file spooled to the printer OK, it pulled a page in, print head went back and forth OK, not enough to account for all the lines, but about enough to account for the paragraphs. Blank page, no text.

I tried printing a page from the help section on the computer, this one had a few links on it to other pages. The page was blank except for the links. It printed the text of the links.

I did a fresh install of Debian 4.0r1 on another box, same thing. The printer works just fine on Win XP on a third box, so it is not a printer issue.

I posted a question on the technical part of the main Ubuntu support page, but no reply after 4 days.

I don't even know where to start with this, it isn't a communication issue, as the pages do go to the printer. It isn't an unrecognized printer, the system knows what it is printing to. There must be a setting somewhere that is telling it not to print text, but how did that get enabled? - and where the heck is it?  This is a new install, I haven't had the time or the inclination to start messing it up - just followed all directions

Help, Please!!

---

### Post by 11hjpphty76lkjj on 2007-12-04
Please run:

```
hp-check -t
```

and post the output.

A

---

### Post by Pierre Fortier on 2007-12-05
Hello, thanks for the reply.

On the other hand, I don't know what to do with that string of commands.

I opened a terminal, typed it in as written, and got:
bash: hp-check: command not found

I tried run hp-check -t and got:
bash: run: command not found

Is there a special place to run this that I don't know about?

thanks

---

### Post by 11hjpphty76lkjj on 2007-12-05
Actually that means you are using the prepackaged version of hplip.  You may want to remove it,

```
sudo apt-get remove hplip
```and install the latest version of hplip from [http://hplip.sf.net](http://hplip.sf.net).  It's really easy and ubuntu is fully supported through the automated installer.

Hope this helps.

A

---

### Post by Pierre Fortier on 2007-12-05
OK, I installed the new version of hplip, printed a test page, got the same results - good graphics, no text, so I ran the code from your original message. The output is as follows:
pnp@ubuntu:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 2.7.10)
Dependency/Version Check Utility ver. 12.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

Distribution:
ubuntu 7.10

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.1 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
OK, Version 4.7 installed

Checking for CUPS...
Status: scheduler is running
Version: 1.3.2

Checking for Reportlab...
OK, version >= 2.0

----------------
| DEPENDENCIES |
----------------


Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-devel - Python development files...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
warning: NOT FOUND! This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsane

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.7.10 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.7.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-2.7.10
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
foomatic=/usr/share/foomatic

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-xml-install=yes
foomatic-ppd-install=no
internal-tag=2.7.10.11


----------------------
| INSTALLED PRINTERS |
----------------------

 
DESKJET_930C
------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/DeskJet_930C?serial=MY068152H8JL
PPD: /etc/cups/ppd/DESKJET_930C.ppd
PPD Description: HP DeskJet 930C Foomatic/hpijs (recommended)
Printer status: printer DESKJET_930C is idle.  enabled since Wed 05 Dec 2007 05:55:29 PM MST

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
error: scanimage not found.

---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
HP Device 0x1204 at 002:002: 
    Device URI: hp:/usb/DeskJet_930C?serial=MY068152H8JL
    Device node: /dev/bus/usb/002/002
    Mode: 0666

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --yes --force-yes libsane

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


The only error it had referred to sane, a scanner system that does not support the old UMAX Astra scanner that I have, so that should not pose a problem, should it?

I also rebooted the system after the update of hplip, just in case that would help.

---

### Post by 11hjpphty76lkjj on 2007-12-06
Hmm everything looks fine.

Try removing ghostscript and re-installing.  I don't think this is an HPLIP problem, but it may be a ghostscript or foomatic problem.

```
sudo apt-get remove gs
```

```
sudo apt-get install gs
```

```
sudo apt-get remove foomatic-db foomatic-db-engine foomatic-db-hpijs
```

```
sudo apt-get install foomatic-db foomatic-db-engine foomatic-db-hpijs
```

---

### Post by Pierre Fortier on 2007-12-06
OK, I tried the above, and am attaching the results:

pnp@ubuntu:~$ sudo apt-get remove gs
[sudo] password for pnp:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gs is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-qt3 python-sip4 libqt3-mt libaudio2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pnp@ubuntu:~$ sudo apt-get install gs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-qt3 python-sip4 libqt3-mt libaudio2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.0kB of archives.
After unpacking, 49.2kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main gs 8.61.dfsg.1~svn8187-0ubuntu3.2 [18.0kB]
Fetched 18.0kB in 0s (23.7kB/s)
Selecting previously deselected package gs.
(Reading database ... 101216 files and directories currently installed.)
Unpacking gs (from .../gs_8.61.dfsg.1~svn8187-0ubuntu3.2_all.deb) ...
Setting up gs (8.61.dfsg.1~svn8187-0ubuntu3.2) ...


pnp@ubuntu:~$ sudo apt-get remove foomatic-db foomatic-db-engine foomatic-db-hpijsReading package lists... Done
Building dependency tree       
Reading state information... Done
Package foomatic-db-hpijs is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-ipy python-qt3 python-sip4 libqt3-mt libaudio2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  foomatic-db foomatic-db-engine foomatic-gui python-foomatic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 13.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 101219 files and directories currently installed.)
Removing foomatic-gui ...
Removing python-foomatic ...
Removing foomatic-db-engine ...
Removing foomatic-db ...
dpkg - warning: while removing foomatic-db, directory `/usr/share/foomatic/db/source/opt' not empty so not removed.
dpkg - warning: while removing foomatic-db, directory `/usr/share/foomatic/db/source/driver' not empty so not removed.
dpkg - warning: while removing foomatic-db, directory `/usr/share/foomatic/db/source/printer' not empty so not removed.
dpkg - warning: while removing foomatic-db, directory `/usr/share/foomatic/db/source' not empty so not removed.
dpkg - warning: while removing foomatic-db, directory `/usr/share/foomatic/db' not empty so not removed.
pnp@ubuntu:~$  sudo apt-get install foomatic-db foomatic-db-engine foomatic-db-hpijs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-ipy python-qt3 python-sip4 libqt3-mt libaudio2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  hpijs
Suggested packages:
  foomatic-db-gutenprint foomatic-gui hplip hpoj hpijs-ppds
The following NEW packages will be installed:
  foomatic-db foomatic-db-engine foomatic-db-hpijs hpijs
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1445kB of archives.
After unpacking, 19.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)'
in the drive '/cdrom/' and press enter

Selecting previously deselected package foomatic-db.
(Reading database ... 98427 files and directories currently installed.)
Unpacking foomatic-db (from .../foomatic-db_20070919-0ubuntu3_all.deb) ...
Selecting previously deselected package foomatic-db-engine.
Unpacking foomatic-db-engine (from .../foomatic-db-engine_3.0.2-20070719-0ubuntu4_amd64.deb) ...
Selecting previously deselected package hpijs.
Unpacking hpijs (from .../hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5_amd64.deb) ...
Selecting previously deselected package foomatic-db-hpijs.
Unpacking foomatic-db-hpijs (from .../foomatic-db-hpijs_20070813-0ubuntu1_all.deb) ...
Setting up foomatic-db (20070919-0ubuntu3) ...
Setting up foomatic-db-engine (3.0.2-20070719-0ubuntu4) ...
Setting up hpijs (2.7.7+2.7.7.dfsg.1-0ubuntu5) ...
Setting up foomatic-db-hpijs (20070813-0ubuntu1) ...

I was hopeful when I read that some of these packages were not installed to start with, but the removal and reinstall did not solve the problem. Is there an internal file somewhere that would tell the print manager software to not include text?

---

