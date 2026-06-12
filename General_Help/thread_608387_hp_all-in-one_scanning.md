---
title: "hp all-in-one scanning"
date: 2007-11-09
forum: General Help
---

### Post by underdog512 on 2007-11-09
I just got a brand new HP C6280 All-in-One printer.  I am running Gutsy.  Ubuntu picked up the printer just fine and prints out flawlessly.  However, I Xsane cannot detect the scanner.  any ideas?

Also the HPLIP Toolbox does not seem to pick up the printer. Its is showing up in CUPS so I don't understand why it is not being picked up by the toolkit. any ideas on this?

---

### Post by underdog512 on 2007-11-10
havn't heard anything on this yet.  Any ideas?

---

### Post by Udibuntu on 2007-11-12
Bump guys,

I also need help with this - same problem with a new C4283.

Thanks,

Udi

---

### Post by Arwen on 2007-11-12
Glad I'm not alone in this,my HP Photosmart C5280 can't be used as a scanner with Xsane either..:-({|=
I tried through Preferences->Load Device Settings in xsane to select "Hewlett-Packard:Photosmart__C5200__series.drc" but when I clicked scan it said "Failed to start scanner invalid argument"

Is there any other program like xsane which we can use?

---

### Post by 11hjpphty76lkjj on 2007-11-13
Can you run hp-check and post the output?

Also if you can run the printingbuginfo script and include that info as well.

[https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)

A

---

### Post by Arwen on 2007-11-14
hp-check gives:


[01mHP Linux Imaging and Printing System (ver. 2.7.10)[0m
[01mDependency/Version Check Utility ver. 12.0[0m

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Saving output in log file: hp-check.log

Initializing. Please wait...

---------------
| SYSTEM INFO |
---------------

[01mBasic system information:[0m
Linux Nemo 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux


[01mDistribution:[0m
ubuntu 7.04
[01m
HPOJ running?[0m
No, HPOJ is not running (OK).

[01mChecking Python version...[0m
OK, version 2.5.1 installed

[01mChecking PyQt version...[0m
OK, version 3.17 installed.

[01mChecking SIP version...[0m
OK, Version 4.5 installed

[01mChecking for CUPS...[0m
Status: scheduler is running
Version: 1.2.8

[01mChecking for Reportlab...[0m
OK, version >= 2.0

----------------
| DEPENDENCIES |
----------------


[01mChecking for dependency: cups - Common Unix Printing System...[0m
OK, found.

[01mChecking for dependency: cups-devel- Common Unix Printing System development files...[0m
OK, found.

[01mChecking for dependency: gcc - GNU Project C and C++ Compiler...[0m
OK, found.

[01mChecking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...[0m
OK, found.

[01mChecking for dependency: libcrypto - OpenSSL cryptographic library...[0m
OK, found.

[01mChecking for dependency: libjpeg - JPEG library...[0m
OK, found.

[01mChecking for dependency: libnetsnmp-devel - SNMP networking library development files...[0m
OK, found.

[01mChecking for dependency: libpthread - POSIX threads library...[0m
OK, found.

[01mChecking for dependency: libtool - Library building support services...[0m
OK, found.

[01mChecking for dependency: libusb - USB library...[0m
OK, found.

[01mChecking for dependency: make - GNU make utility to maintain groups of programs...[0m
OK, found.

[01mChecking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...[0m
OK, found.

[01mChecking for dependency: ppdev - Parallel port support kernel module....[0m
OK, found.

[01mChecking for dependency: PyQt - Qt interface for Python...[0m
OK, found.

[01mChecking for dependency: python-devel - Python development files...[0m
OK, found.

[01mChecking for dependency: Python 2.3 or greater - Required for fax functionality...[0m
OK, found.

[01mChecking for dependency: Python 2.2 or greater - Python programming language...[0m
OK, found.

[01mChecking for dependency: Reportlab - PDF library for Python...[0m
OK, found.

[01mChecking for dependency: SANE - Scanning library...[0m
OK, found.

[01mChecking for dependency: SANE - Scanning library development files...[0m
OK, found.

[01mChecking for dependency: scanimage - Shell scanning program...[0m
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsane

[01mChecking for dependency: xsane - Graphical scanner frontend for SANE...[0m
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


[01mCurrently installed HPLIP version...[0m
HPLIP 2.7.10 currently installed in '/usr/share/hplip'.

[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
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
pp-build=yes
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


[01mPhotosmart_C5280[0m
[01m----------------[0m
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Photosmart_C5200_series?serial=MY74BBF0FR04XQ
PPD: /etc/cups/ppd/Photosmart_C5280.ppd
PPD Description: HP PhotoSmart C5200 Foomatic/hpijs (recommended)
Printer status: printer Photosmart_C5280 is idle.  enabled since &#931;&#945;&#946; 27 &#927;&#954;&#964; 2007 12:33:54 &#956;&#956; EEST

[01mStylus-C46[0m
[01m----------[0m
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://EPSON/Stylus%20C46
PPD: /etc/cups/ppd/Stylus-C46.ppd
PPD Description: Epson Stylus C46 - CUPS+Gutenprint v5.0.0.99.1
Printer status: printer Stylus-C46 is idle.  enabled since &#931;&#945;&#946; 30 &#921;&#959;&#973;&#957; 2007 10:51:14 &#960;&#956; EEST


----------------------
| SANE CONFIGURATION |
----------------------

[01m'hpaio' in '/etc/sane.d/dll.conf'...[0m
OK, found. SANE backend 'hpaio' is properly set up.

[01mChecking output of 'scanimage -L'...[0m

---------------------
| PYTHON EXTENSIONS |
---------------------

[01mChecking 'cupsext' CUPS extension...[0m
OK, found.

[01mChecking 'pcardext' Photocard extension...[0m
OK, found.

[01mChecking 'hpmudext' I/O extension...[0m
OK, found.

[01mChecking 'scanext' SANE scanning extension...[0m
OK, found.


-----------------
| USB I/O SETUP |
-----------------


[01mChecking for permissions of USB attached printers...[0m

-----------
| SUMMARY |
-----------


[01mSummary of needed commands to run to satisfy missing dependencies:[0m
sudo apt-get install --yes --force-yes libsane

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

warning: NOT FOUND! This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
error: scanimage not found.
error: 2 errors and/or warnings.
I will post printingbuginfo.txt in a while

---

### Post by Arwen on 2007-11-14
Here it's printingbuginfo.txt:

ProblemType: printingbuginfo v2.0: printingbug+localusb ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
CupsConfiguredDevices:
 device for Photosmart_C5280: hp:/usb/Photosmart_C5200_series?serial=MY74BBF0FR04XQ
 device for Stylus-C46: usb://EPSON/Stylus%20C46
CupsConfiguredPPDs:
 Photosmart_C5280: HP PhotoSmart C5200 Foomatic/hpijs (recommended)
 Stylus-C46: Epson Stylus C46 - CUPS+Gutenprint v5.0.0.99.1
Date: Wed Nov 14 12:41:43 2007
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 7.04
EtcPapersize: a4
InstalledPrintingPackages:
 ii  cupsys                   1.2.8-0ubuntu8.1         Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.0.99.1-0ubuntu2      printer drivers for CUPS
 ii  foo2zjs                  20061224-0ubuntu3        Support for printing to ZjStream-based printers
 ii  foomatic-db              20070327-0ubuntu1        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070303-0ubuntu1  OpenPrinting printer support - programs
 ii  foomatic-filters         3.0.2-20070323-0ubuntu1  OpenPrinting printer support - filters
 ii  gnome-cups-manager       0.31-3ubuntu5            CUPS printer admin tool for GNOME
 ii  gs-common                0.3.11ubuntu1            Common files for different Ghostscript releases
 ii  gs-esp                   8.15.4.dfsg.1-0ubuntu1   The Ghostscript PostScript interpreter - ESP version
 ii  gs-esp-x                 8.15.4.dfsg.1-0ubuntu1   The Ghostscript PostScript interpreter - ESP version
 ii  libgnomeprint2.2-0       2.18.0-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20070327-0ubuntu1        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
Locale: LANG=el_GR.UTF-8, LC_CTYPE=el_GR.UTF-8, LC_PAPER=el_GR.UTF-8
Uname: Linux Nemo 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux
UsbPrinterDevices: crw-rw---- 1 root lp 180, 0 Nov 14 12:41 /dev/usblp0
UsbPrinterIEEE1284Id:
 /dev/usblp0: GET_DEVICE_ID string:
 MFG:HP;MDL:Photosmart C5200 series;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;1284.4DL:4d,4e,1;CLS:PRINTER;DES:Q8330B;SN:MY74BBF0FR04XQ;S:038008C484001021012c1800012c288004a;J:                    ;Z:0102,0503e809016bc9,0600,0c100,0e00,0f00;
UsbPrinterKernelModules:
 usblp                  14848  0 
 usbcore               134280  10 usb_storage,usblp,libusual,gspca,zc0301,ueagle_atm,usbatm,ehci_hcd,uhci_hcd
lsusb:
 Bus 005 Device 005: ID 03f0:5d11 Hewlett-Packard 
 Bus 005 Device 001: ID 0000:0000  
 Bus 002 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn) 
 Bus 002 Device 001: ID 0000:0000  
 Bus 003 Device 001: ID 0000:0000  
 Bus 001 Device 004: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
 Bus 001 Device 001: ID 0000:0000  
 Bus 004 Device 001: ID 0000:0000  

THAT'S IT!

---

### Post by bumanie on 2007-11-14
I haven't used gutsy yet, but I suspect you could go to HP website and download a deb. file or may be even find command line instructions. They have these for feisty -not sure about gutsy, but would be surprised if there was no deb. files at the very least.

---

### Post by 11hjpphty76lkjj on 2007-11-14
Actually the HPLIP project doesn't create deb or RPM files.  We leave that up to the distros and provide only the source. However there is extensive install instructions and an automatic installer.

Arwen:

Seems you are missing scanimage.  Try running

```
sudo apt-get install sane sane-utils
```

and then try scanning.

A

---

### Post by Arwen on 2007-11-14
It fails again but when I try to remove from Preferences Noname:CreativeLive!.drc(I don't know why but it tries to do sth with my webcam and when I click on Scan,here comes out a photo of me gazing on the screen!:-P) and  to replace it with HewlettPackard:Photosmart_C5200_series.drc it won't ever do that. :-S

---

### Post by 11hjpphty76lkjj on 2007-11-14
Sorry--when you hit scan your webcam takes a pic?  

Something is very odd...possible to uninstall hplip

```
sudo apt-get remove hplip
```

and install from source?
```

http://hplip.sf.net
```

It's pretty easy for ubuntu...

A

---

### Post by 11hjpphty76lkjj on 2007-11-14
sorry you may have done that already...perhaps unplug the webcam, delete the printing queue and re-install it by running 
```

sudo hp-setup
```

A

---

### Post by Arwen on 2007-11-14
> Sorry--when you hit scan your webcam takes a pic? 
Yes that's what it does.
> delete the printing queue 
How to delete that and what is that?

---

### Post by 11hjpphty76lkjj on 2007-11-14
You can try running hp-toolbox, click the printer and then delete.  Or you can delete it through the cups interface:

[http://localhost:631](http://localhost:631)

hope this helps!
A

---

### Post by Arwen on 2007-11-14
OK I don't have much time now so I'll check it out probably tomorrow again(this time with the webcam unplugged).Thank you for your time,I will post if it works finally.:-)

---

### Post by underdog512 on 2007-11-20
> **kalosaurusrex said:**
> Actually the HPLIP project doesn't create deb or RPM files.  We leave that up to the distros and provide only the source. However there is extensive install instructions and an automatic installer.

Arwen:

Seems you are missing scanimage.  Try running

```
sudo apt-get install sane sane-utils
```

and then try scanning.

A

Xsane still will not pick up my scanner

---

### Post by underdog512 on 2007-11-20
> **underdog512 said:**
> 

Also the HPLIP Toolbox does not seem to pick up the printer. Its is showing up in CUPS so I don't understand why it is not being picked up by the toolkit. any ideas on this?

By the way, I tried finding the printer manually and complete the hp-setup process but upon completion of hp-setup I get an error stating that "Printer is busy, offline,or in an error state"

---

### Post by 11hjpphty76lkjj on 2007-11-21
> By the way, I tried finding the printer manually and complete the hp-setup process but upon completion of hp-setup I get an error stating that "Printer is busy, offline,or in an error state"

Try power cycling the printer? same results?

---

### Post by underdog512 on 2007-12-01
yes

---

### Post by midijery on 2008-04-23
Have you tried turning off guarddog there seem's to be problem if the firewall is activated. I just did an install of a HP Photosmart c6280 and it was the the most painless install of an HP Printer I've ever had (no command line Arguements or console necessary. I'm using "Kubuntu-8.04-beta-desktop_Amd-64" and had more than 200 patches done to it through "Adept" in the last couple of days so I assume it is getting near completion. Anyway they seem to have it right this time for the HP printers. No firewall problems and everything went pretty much automatically.
Many thank's to the developers for a very good job. 
Jerry

---

