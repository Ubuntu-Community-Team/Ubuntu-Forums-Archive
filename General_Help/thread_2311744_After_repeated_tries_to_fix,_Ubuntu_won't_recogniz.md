---
title: "After repeated tries to fix, Ubuntu won't recognize HP printer after update"
date: 2016-01-29
forum: General Help
---

### Post by Javelin Dan on 2016-01-29
After a recent kernal update of Ubuntu 12.04 on my Compaq Presario CQ61-313US notebook, my HP Photosmart D110 which previously printed and scanned flawlessly is no longer recognized in any of the USB ports which all function using other devices. I also have Lubuntu 14.04 installed on another partition of this computer, and the same problem exists there as well.
 

 I've been researching this problem heavily, and it seems to be prevalent with the newer versions/updates of Ubuntu (and Linux Mint) and HP printers. Unfortunately, non of the remedies I've seen and tried have worked for me. Running the command “sudo hp-setup” yields the following output:
 
```

 ***********Presario-CQ61-Notebook-PC:~$ sudo hp-setup 
  HP Linux Imaging and Printing System (ver. 3.13.11) 
 Printer/Fax Setup Utility ver. 9.0 
  Copyright (c) 2001-9 Hewlett-Packard Development Company, LP 
 This software comes with ABSOLUTELY NO WARRANTY. 
 This is free software, and you are welcome to distribute it 
 under certain conditions. See COPYING file for more details. 
  Searching... (bus=usb, search=(None), desc=0) 
 error: No devices found on bus: usb 
  Done. 
 

```
 I also entered the command: “sudo hp-check -r”. The full verbose output is pasted below. However, one thing that caught my attention was the following line:  
 
```

 --------------- 
 | USER GROUPS | 
 --------------- 
  root 
  error: User needs to be member of group 'lp' to enable print, scan & fax. 
 error: User needs to be member of group 'lpadmin' to manage printers. 
 
```

 So I went into “Users and Groups” and added authorization for these two headings. No change, still the same output from “sudo hp-setup”. This printer still shows up as installed with a green check mark in the "Printing" utility of the "System Tools" application. Trying to install the printer for the first time in Lubuntu 14.04, the options list is empty and the printer doesn't appear at all. I'm completely stumped and could use some help, please.  
 

 (Full output of “ sudo hp-check -r” shown below)
 

 
```

 ***********Presario-CQ61-Notebook-PC:~$ sudo hp-check -r 
  HP Linux Imaging and Printing System (ver. 3.13.11) 
 Dependency/Version Check Utility ver. 14.3 
  Copyright (c) 2011-14 Hewlett-Packard Development Company, LP 
 This software comes with ABSOLUTELY NO WARRANTY. 
 This is free software, and you are welcome to distribute it 
 under certain conditions. See COPYING file for more details. 
  Note: hp-check can be run in three modes: 
 1. Compile-time check mode (-c or --compile): Use this mode before compiling the 
 HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies 
 are installed to successfully compile HPLIP.                                     
 2. Run-time check mode (-r or --run): Use this mode to determine if a distro     
 supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball    
 has the proper dependencies installed to successfully run.                       
 3. Both compile- and run-time check mode (-b or --both) (Default): This mode     
 will check both of the above cases (both compile- and run-time dependencies).    
  Saving output in log file: hp-check.log 
  Initializing. Please wait... 
  
 --------------- 
 | SYSTEM INFO | 
 --------------- 
  Basic system information: 
 Linux daniel-Presario-CQ61-Notebook-PC 3.2.0-97-generic-pae #137-Ubuntu SMP Thu Dec 17 21:37:53 UTC 2015 i686 athlon i386 GNU/Linux 
  Distribution: 
 ubuntu 12.04 
  Checking Python version... 
 OK, version 2.7.3 installed 
  Checking PyQt 4.x version... 
 OK, version 4.9.1 installed. 
  Checking for CUPS... 
 Status: scheduler is running 
 Version: 1.5.3 
 error_log is set to level: warn 
  Checking for dbus/python-dbus... 
 dbus daemon is running. 
 python-dbus version: 1.0.0 
   ------------------------ 
 | RUNTIME DEPENDENCIES | 
 ------------------------ 
   Checking for dependency: CUPS - Common Unix Printing System... 
 OK, found. 
  Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer... 
 OK, found. 
  Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)... 
 OK, found. 
  Checking for dependency: PolicyKit - Administrative policy framework... 
 OK, found. 
  Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4... 
 OK, found. 
  Checking for dependency: Python DBus - Python bindings for DBus... 
 OK, found. 
  Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications... 
 OK, found. 
  Checking for dependency: Python XML libraries... 
 OK, found. 
  Checking for dependency: Python 2.3 or greater - Required for fax functionality... 
 OK, found. 
  Checking for dependency: Reportlab - PDF library for Python... 
 OK, found. 
  Checking for dependency: SANE - Scanning library... 
 OK, found. 
  Checking for dependency: scanimage - Shell scanning program... 
 OK, found. 
  Checking for dependency: xsane - Graphical scanner frontend for SANE... 
 OK, found. 
   ---------------------- 
 | HPLIP INSTALLATION | 
 ---------------------- 
   Currently installed HPLIP version... 
 HPLIP 3.13.11 currently installed in '/usr/share/hplip'. 
  Current contents of '/etc/hp/hplip.conf' file: 
 # hplip.conf.  Generated from hplip.conf.in by configure. 
  [hplip] 
 version=3.13.11 
  [dirs] 
 home=/usr/share/hplip 
 run=/var/run 
 ppd=/usr/share/ppd/hplip/HP 
 ppdbase=/usr/share/ppd/hplip 
 doc=/usr/share/doc/hplip-3.13.11 
 html=/usr/share/doc/hplip-3.13.11 
 icon=/usr/share/applications 
 cupsbackend=/usr/lib/cups/backend 
 cupsfilter=/usr/lib/cups/filter 
 drv=/usr/share/cups/drv/hp 
 bin=/usr/bin 
  # Following values are determined at configure time and cannot be changed. 
 [configure] 
 network-build=yes 
 libusb01-build=no 
 pp-build=no 
 gui-build=yes 
 scanner-build=yes 
 fax-build=yes 
 dbus-build=yes 
 cups11-build=no 
 doc-build=yes 
 shadow-build=no 
 hpijs-install=no 
 foomatic-drv-install=no 
 foomatic-ppd-install=no 
 foomatic-rip-hplip-install=no 
 hpcups-install=yes 
 cups-drv-install=yes 
 cups-ppd-install=no 
 internal-tag=3.13.11 
 restricted-build=no 
 ui-toolkit=qt4 
 qt3=no 
 qt4=yes 
 policy-kit=no 
 lite-build=no 
 udev-acl-rules=yes 
 udev_sysfs_rules=no 
 hpcups-only-build=no 
 hpijs-only-build=no 
   Current contents of '/var/lib/hp/hplip.state' file: 
 # hplip.state - HPLIP runtime persistent variables.  
  [plugin] 
 installed=0 
 eula=0 
    Current contents of '~/.hplip/hplip.conf' file: 
 [upgrade] 
 notify_upgrade = false 
 last_upgraded_time = 1385081916 
 pending_upgrade_time = 0 
 latest_available_version = 3.13.11 
  [installation] 
 date_time = 11/21/2013 19:52:39 
 version = 3.13.11 
    -------------------------- 
 | DISCOVERED USB DEVICES | 
 -------------------------- 
  No devices found. 
  --------------------------------- 
 | INSTALLED CUPS PRINTER QUEUES | 
 --------------------------------- 
   
 Deskjet_3510 
 ------------ 
 Type: Printer 
 Device URI: hp:/usb/Deskjet_3510_series?serial=CN2B51PGS105R7 
 PPD: /etc/cups/ppd/Deskjet_3510.ppd 
 PPD Description: HP Deskjet 3510 Series, hpcups 3.13.7 
 Printer status: printer Deskjet_3510 is idle.  enabled since Mon 04 Nov 2013 08:43:59 PM EST 
 error: Unsupported model: Deskjet_3510_series 
 error: Communication status: Failed 
  HP-Photosmart-D110-series 
 ------------------------- 
 Type: Printer 
 Device URI: hp:/net/Photosmart_D110_series?zc=HPE0996A 
 PPD: /etc/cups/ppd/HP-Photosmart-D110-series.ppd 
 PPD Description: HP Photosmart d110 Series, hpcups 3.12.2 
 Printer status: printer HP-Photosmart-D110-series is idle.  enabled since Tue 10 Mar 2015 02:19:31 PM EDT 
 error: Unable to communicate with device (code=12): hp:/net/Photosmart_D110_series?zc=HPE0996A 
 error: unable to open channel 
 error: Communication status: Failed 
   ---------------------- 
 | SANE CONFIGURATION | 
 ---------------------- 
  'hpaio' in '/etc/sane.d/dll.conf'... 
 OK, found. SANE backend 'hpaio' is properly set up. 
  Checking output of 'scanimage -L'... 
 device `hpaio:/net/Photosmart_D110_series?zc=HPE0996A' is a Hewlett-Packard Photosmart_D110_series all-in-one 
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
    
 --------------- 
 | USER GROUPS | 
 --------------- 
  root 
  error: User needs to be member of group 'lp' to enable print, scan & fax. 
 error: User needs to be member of group 'lpadmin' to manage printers. 
  ----------- 
 | SUMMARY | 
 ----------- 
  error: 2 errors and/or warnings. 
  Please refer to the installation instructions at: 
 [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html) 
   Done. 
```

---

### Post by Habitual on 2016-01-29
After you added yourself to lp and lpadmin , did you login and back in for the changes to take affect?

---

### Post by Javelin Dan on 2016-01-29
I didn't think of it till you suggested it, but did just now and no change. "No devices found..."

---

### Post by Javelin Dan on 2016-01-30
I decided to try to reinstall using the "hplip-3.13.9.run" driver (saw it suggested in another thread). At the end of it, I got the following message:
```

error: hp-setup failed. Please run hp-setup manually

```
I did, and got the following output:
```

                         PRINTER SETUP 

 ------------- 
 Please make sure your printer is connected and powered on at this time. 
 error: hp-setup failed. Please run hp-setup manually. 
  
  
 RE-STARTING HP_SYSTRAY 

 ---------------------- 
  
 HP Linux Imaging and Printing System (ver. 3.13.9) 
 System Tray Status Service ver. 2.0 
  
 Copyright (c) 2001-13 Hewlett-Packard Development Company, LP 
 This software comes with ABSOLUTELY NO WARRANTY. 
 This is free software, and you are welcome to distribute it 
 under certain conditions. See COPYING file for more details. 
  
 /usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK 
   set_interactive(1) 
 /usr/share/hplip/hplip_clean.sh: 44: [: -gt: unexpected operator 
 user@user-Presario-CQ61-Notebook-PC:~/Desktop$ sudo hp-setup 
  

```

---

