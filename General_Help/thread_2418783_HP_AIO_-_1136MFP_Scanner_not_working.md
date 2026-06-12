---
title: "HP AIO - 1136MFP Scanner not working"
date: 2019-05-11
forum: General Help
---

### Post by jatin21 on 2019-05-11
Hi,

I am on Ubuntu 19.04 and trying to get HP 1136 MFP scanner working. I have already installed hplip-3.19.3 but not able to get scanner to work despite going through several topics on this forum and stack-overflow. I am including debug outputs from various utilities as follows:

Any help will be greatly appreciated!

[B]hp-scan
[/B]```

hp-scan

HP Linux Imaging and Printing System (ver. 3.19.3)
Scan Utility ver. 2.2


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


warning: No destinations specified. Adding 'file' destination by default.
Using device hpaio:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c
Opening connection to device...
error: SANE: Error during device I/O (code=9)


```

**xsane 0.999**
```
Failed to open device 'hpaio:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c': Error during device I/O.
```

[B]hp-check
```


```[/B]```
HP Linux Imaging and Printing System (ver. 3.19.3)
Dependency/Version Check Utility ver. 15.1


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed 
to successfully compile HPLIP.                                                                                                                                                  
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper       
dependencies installed to successfully run.                                                                                                                                     
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).                      


Check types:                                                                                                                                                                    
a. EXTERNALDEP - External Dependencies                                                                                                                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)                                                                                                    
c. COMPILEDEP - Compile time Dependencies                                                                                                                                       
d. [All are run-time checks]                                                                                                                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                                                                                                                


Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version


warning: 12-19.04 version is not supported. Using 12-18.10 versions dependencies to verify and install...


---------------
| SYSTEM INFO |
---------------


 Kernel: 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 GNU/Linux
 Host: BTS
 Proc: 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 GNU/Linux
 Distribution: 12 19.04
 Bitness: 64 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.19.3
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for 12 distro  19.04 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.19.3


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.19.3
html=/usr/share/doc/hplip-3.19.3
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin
apparmor=/etc/apparmor.d
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
internal-tag=3.19.3
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no
class-driver=no




Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.19.3






Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = false
last_upgraded_time = 1557417722
pending_upgrade_time = 0
latest_available_version = 3.17.10


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hp:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c"
printer_name = 
working_dir = .


[commands]
scan = /usr/bin/xsane -V %SANE_URI%


[refresh]
rate = 30
enable = false
type = 1


[polling]
enable = false
interval = 5
device_list = 


[fax]
voice_phone = 
email_address = 


[installation]
date_time = 11/05/19 14:50:40
version = 3.19.3




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------
| COMPILEDEP |
--------------


 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               8.3.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.2.1           OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -


------------------------
| General Dependencies |
------------------------


 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.1           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.2.6           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.12.1          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.29            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.16          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.10          OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.8           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.5.18          OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.12.1          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.10          OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.16          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -


----------------------
| Scan Configuration |
----------------------


 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.19.3          OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.19.3          OK         'hpaio found in /etc/sane.d/dll.conf'


-------------------------
| External Dependencies |
-------------------------


 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.26            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.27          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.10          OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.20.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.12.12         OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.7             OK         -


---------------------
| Python Extentions |
---------------------


 hpmudext             IO-Extension                                                 REQUIRED        -               3.19.3          OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.19.3          OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c' is a Hewlett-Packard HP_LaserJet_Professional_M1136_MFP all-in-one
device `hpaio:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c' is a Hewlett-Packard HP_LaserJet_Professional_M1136_MFP all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


  Device URI                                                              Model                              
  ----------------------------------------------------------------------  -----------------------------------
  hp:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c  HP LaserJet Professional M1136 MFP 


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HL-L2320D
---------
Type: Unknown
Device URI: usb://Brother/HL-L2320D%20series?serial=E73793G7N903101
PPD: /etc/cups/ppd/HL-L2320D.ppd
warning: Failed to read /etc/cups/ppd/HL-L2320D.ppd ppd file
PPD Description: 
Printer status: printer HL-L2320D is idle.  enabled since Saturday 11 May 2019 02:46:01 PM IST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.


HP-LaserJet-Professional-M1136-MFP
----------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1136_MFP?serial=000000000QH9D9ATSI1c
PPD: /etc/cups/ppd/HP-LaserJet-Professional-M1136-MFP.ppd
PPD Description: HP LaserJet Professional m1136 MFP, hpcups 3.19.1, requires proprietary plugin
Printer status: printer HP-LaserJet-Professional-M1136-MFP is idle.  enabled since Friday 10 May 2019 01:16:18 PM IST
Communication status: Good




--------------
| PERMISSION |
--------------


USB             HP-LaserJet-Professional-M1136-MFP Required        -        -        OK       Node:'/dev/bus/usb/003/007' Perm:'  root  lp rwx rw- rw- rwx r-x'
 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
None


Missing Optional Dependencies
-----------------------------
None




Total Errors: 0
Total Warnings: 1




Done.

```

[B]Thanks!!
[/B]

---

