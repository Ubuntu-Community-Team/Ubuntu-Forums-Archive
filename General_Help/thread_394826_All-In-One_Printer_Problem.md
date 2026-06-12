---
title: "All-In-One Printer Problem"
date: 2007-03-27
forum: General Help
---

### Post by BoneyOne on 2007-03-27
I recently brought my sisters Trojan/Virus/Botnet laden Windows PC over to my place to fix it. I grew tired of all of the hassle and decided to toss Ubuntu on her machine.

All went well, I even loaded up my printer on her machine as she has the same exactly printer (HP PSC 1610). I was able to print/scan/transfer pics on mine.

I took it back to her house, and had to install her printer separately still. Now I can't print (goes into a job hold status) , can't scan (program can't find the device), but can go through and transfer pics, can control and view device status from the HP printer utility (HPLIP 1.7.3).

Any ideas?

---

### Post by BoneyOne on 2007-03-28
Well I'm completely clueless, spent a couple of hours today messing with it, same problems.

It seems as if she will be going back to Windows soon, which of course means more work for me trying to keep her computer clean....*sigh*

---

### Post by 11hjpphty76lkjj on 2007-03-29
Can you run hp-check and post the output?

A

---

### Post by dasunst3r on 2007-03-29
Try plugging in your sister's printer and adding it on-site.  After you do that, follow these procedures and I'll explain why:
[list=1]
[*]In your browser, go to [http://localhost:631/printers](http://localhost:631/printers)
[*]There, you should your printer and the printer you just added.  Each one should have an URL that looks like this: ```
usb://HP/PSC%201400%20series?serial={serial number}
```
[/list]
The printer is allegedly not found because her printer's serial number doesn't match yours.  In any case, go back to your printer GUI and delete the first printer you added.  Set her printer to default, and everything should be just peachy!

---

### Post by 11hjpphty76lkjj on 2007-03-29
I'm sorry but this is incorrect.

As he stated he's using HPLIP 1.7.3 your direction will not work.  

The HPLIP backend uses the hp:// uri. the usb:// is for the cups backend, using the cups backend will remove a lot of extended funtionality that HPLIP provides.

Really if he runs hp-check and sends me the log I can most probably direct him to the cause of the problem.  

He could also try running hp-toolbox, removing all printers listed, and run hp-setup to re-add the printer.

---

### Post by BoneyOne on 2007-04-02
Sorry for the delay. I'll run the hp-check and post the info up here shortly.
I've done the toolbox, removing all and then running hp-setup to re-add, it only gives me the same symptoms.

---

### Post by BoneyOne on 2007-04-03
> HP Linux Imaging and Printing System (ver. 1.7.3)
Dependency/Version Check Utility ver. 5.3

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux Maries-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Detected distro (/etc/issue):
ubuntu 6.10

Detected distro (lsb_release):
Ubuntu 6.10 (edgy)

Currently installed HPLIP version...
HPLIP 1.7.3 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf

[hpiod]
# port=0 (dynamic IP port)
port=2208
[hpssd]
# port=0 (dynamic IP port)
port=2207

[hplip]
version=1.7.3
jdprobe=0

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-1.7.3

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=1
pp-build=0
gui-build=1
scanner-build=1
fax-build=1
cups11-build=0
installinitd=/usr/lib/lsb/install_initd
chkconfig=
internal-tag=1.7.3.14


HPLIP running?
No, HPLIP is not running (OK).

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.4.4 installed

Checking PyQt version...
OK, version 3.16 installed.

Checking SIP version...
OK, Version 4.4.5 installed

----------------
| DEPENDENCIES |
----------------

 
Checking for dependency libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency SANE - Scanning library...
OK, found.

Checking for dependency GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency libjpeg - JPEG library...
OK, found.

Checking for dependency libpthread - POSIX threads library...
OK, found.

Checking for dependency make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency python-devel - Python development files...
OK, found.

Checking for dependency Reportlab - PDF library for Python...
OK, found.

Checking for dependency PyQt - Qt interface for Python...
OK, found.

Checking for dependency cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency ppdev - Parallel port support kernel module....
error: Not found!
This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.

Checking for dependency libusb - USB library...
OK, found.

Checking for dependency scanimage - Shell scanning program...
OK, found.

Checking for dependency libnetsnmp-devel - SNMP networking library development files...
error: Not found!
error: This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency LSB - Linux Standard Base support...
OK, found.

Checking for dependency xsane - Graphical scanner frontend for SANE...
OK, found.

Checking for dependency cups - Common Unix Printing System...
OK, found.

Checking for dependency Python 2.3 or greater - Required for fax functionality...
OK, found.


----------------------
| INSTALLED PRINTERS |
----------------------

 
PSC_1600
--------
Device URI: hp:/usb/PSC_1600_series?serial=MY56RD32F6L0
Installed in HPLIP? Yes
PPD: /etc/cups/ppd/PSC_1600.ppd
PPD Description: HP PSC 1600 Foomatic/hpijs (recommended)
Printer status: printer PSC_1600 is idle.  enabled since Mon 26 Mar 2007 08:45:59 PM CDT



----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.


2 errors were detected.[]("http://hplip.sourceforge.net/install/index.html")
Now I noticed that it states that libnetsnmp-devel is not installed but is required. I attempted to find libnetsnmp in Synaptic but it wasn't listed. I'm guessing I don't have the right repo. I'm guessing that might have something to do with it, but not sure as I stated that my printer worked.

---

### Post by 11hjpphty76lkjj on 2007-04-03
Actually if you installing the printer ob usb missing libnetsnmp is okay.  libnetsnmp only would cause problem if the printer was connected over the network.

```
 HPLIP running?
No, HPLIP is not running (OK).
```

Could be the problem.

Try restarting hplip and cups,

```
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart
```

delete the printer, and re-add it using

```
sudo hp-setup
```

And let me know how that goes.

---

### Post by BoneyOne on 2007-04-03
Well when restarting hplip I got an error

```
Starting hpiod:                                            [FAILED]
```So I wasn't surprised when I tried to go back into hp-setup when I got another error

```
HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.
```

---

### Post by 11hjpphty76lkjj on 2007-04-03
Run 

```
cat /etc/hosts
```

and post the output.

A

---

