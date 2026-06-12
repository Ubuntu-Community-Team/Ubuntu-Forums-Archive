---
title: "Help to get Xsane recognizing/using network attached scanner"
date: 2007-02-13
forum: General Help
---

### Post by aleska on 2007-02-13
I have an HP Officejet 6110 all-in-one printer/scanner/fax.  It is attached to my network via a usb cable connecting to a buffalo linkstation network storage device running a samba server.  
I have several pcs, all running 6.06 or above.  Printing is no problem.  However, when I run xsane, it scans for devices, then returns an error "no devices available".  

How should I tackle this?  Not sure where to start, and surprisingly I'm having problems finding relevant tutorials (I'd have thought there would be lots of people with network attached scanners).

TIA-
Aleska

---

### Post by the.phantom on 2007-02-13
have you gone to the sane site to see if they have drivers for your scanner?
they seem to be a bit light on scanners supported
after a long afternoon i found out looking around that they do not support my scanner
and that was the error message i got

[http://www.sane-project.org/sane-mfgs.html]("http://www.sane-project.org/sane-mfgs.html")

---

### Post by aleska on 2007-02-14
Thanks for the link.  I checked it out and sure enough xsane doesn't support the HP Officejet 6110, or any officejet all-in-ones for that matter.  
So here is a general plea.  Are there any applications (similar to xsane) for scanning which DO support the officejet 6110 all-in-one printer/fax/scanner?  Am I just out of luck as far as using this particular scanner with a Linux OS?
TIA-
Aleska

---

### Post by leech on 2007-02-17
For the All in One scanners, you have to install HPLIP.  [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)  This lists the Officejet 6110 and supports the scanning.  According to the troubleshooting section on HPLIP's site, it says you have to add hpaio to the /etc/sane.d/dll.conf file.

Leech

---

### Post by ricardisimo on 2007-06-10
I added "hpaio" to /etc/sane.d/dll.conf, and no luck. I keep getting this error:
```
error: 'make' command failed with status code 2
```

If no one minds, I'll post the output from the installer, although not a debugging version...

```
:~ sh hplip-1.7.4a.run
Creating directory hplip-1.7.4a
Verifying archive integrity... All good.
Uncompressing HPLIP 1.7.4a Self Extracting Archive..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
hplip-install_Sun-10-Jun-2007_01:33:50.log

HP Linux Imaging and Printing System (ver. 1.7.4a)
HPLIP Installer ver. 1.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Initializing...

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

INTRODUCTION
------------
This installer will install HPLIP version 1.7.4a on your computer.
Distro is Ubuntu 7.04

ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
note: Password accepted.


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.

Please read the installation notes and hit <enter> to continue (<enter>=continue*, q=quit) : 
Running 'sudo dpkg --configure -a'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes -f '
Please wait, this may take several minutes...
Running 'sudo apt-get update'
Please wait, this may take several minutes...
Running 'xterm -e sudo apt-get install --yes --force-yes postfix'
Please wait, this may take several minutes...
 

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
warning: A previous install of HPLIP is installed and/or running.
Running 'sudo /etc/init.d/hplip stop'
Please wait, this may take several minutes...
 
Running 'sudo apt-get remove --yes --force-yes hplip hpijs'
Please wait, this may take several minutes...
error: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
error: Continuing to run installer - this installation should overwrite the previous one.
 

BUILD AND INSTALL
-----------------

Running './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr'
Please wait, this may take several minutes...
 
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
 
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
 
error: 'make' command failed with status code 2
```

Any help is greatly appreciated. Thanks.

---

