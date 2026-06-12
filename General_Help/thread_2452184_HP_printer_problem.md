---
title: "HP printer problem"
date: 2020-10-18
forum: General Help
---

### Post by zkab on 2020-10-18
After installed 20.04 LTS I have problem with my network printer HP LaserJet Pro M402dne
I get communication errors.
sudo 'hp-check -i' gave me following:
```
forsete@balder:~$ sudo hp-check -i
Saving output in log file: /home/forsete/hp-check.log

HP Linux Imaging and Printing System (ver. 3.20.3)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) 
to determine if the proper dependencies are installed to successfully compile HPLIP.                                      
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an     
already built HPLIP supplied tarball has the proper dependencies installed to successfully run.                           
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both     
compile- and run-time dependencies).                                                                                      

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

warning: ubuntu-20.04 version is not supported. Using ubuntu-19.10 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 5.4.0-51-generic #56-Ubuntu SMP Mon Oct 5 14:28:49 UTC 2020 GNU/Linux
 Host: balder
 Proc: 5.4.0-51-generic #56-Ubuntu SMP Mon Oct 5 14:28:49 UTC 2020 GNU/Linux
 Distribution: ubuntu 20.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.20.3
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  20.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.20.3

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip
html=/usr/share/doc/hplip-doc
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv
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
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.20.3
restricted-build=no
ui-toolkit=qt5
qt3=no
qt4=no
qt5=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no
class-driver=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
warning: Could not access file: No such file or directory
 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.50            OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.29          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.12.16         OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.20.3          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.7             OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               -               OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               -               OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.31'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.8             OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.1           OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.8.5           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             -               MISSING    'python3-pyqt4-dbus needs to be installed'
 error: python3-pyqt4 PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             -               MISSING    'python3-pyqt4 needs to be installed'
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.16          OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.9           OK         -
 error: python3-devel Python devel - Python development files                      REQUIRED        2.2             3.8.5           MISSING    'python3-devel needs to be installed'
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               7.0.0           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.5.34          OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               9.3.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.2.1           OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.20.3          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.20.3          OK         -

----------------------
| Scan Configuration |
----------------------

'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.20.3          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.20.3          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_M402dn
------------------
Type: Printer
Device URI: hp:/net/HP_LaserJet_M402dn?ip=192.168.1.7
PPD: /etc/cups/ppd/HP_LaserJet_M402dn.ppd
PPD Description: HP LaserJet Pro M402-M403 Postscript (recommended)
Printer status: printer HP_LaserJet_M402dn is idle.  enabled since sön 18 okt 2020 13:42:48
Communication status: Good


--------------
| PERMISSION |
--------------

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 

Total Errors: 4
Total Warnings: 1


Done.
forsete@balder:~$ 
```

I have googled alot but can't fix it ... help appreciated.

---

### Post by dragonfly41 on 2020-10-18
My old HP Laser Jet 2100 works on earlier Ubuntu but not on current 20.04.

I compared my output with yours ..

[FONT=monospace][COLOR=#000000]**Missing Required Dependencies**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]**-----------------------------**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FF5454]**error: 'libcups2' package is missing/incompatible **[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#FF5454]**error: 'python3-pyqt4' package is missing/incompatible **[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#FF5454]**error: 'gtk2-engines-pixbuf' package is missing/incompatible **[/COLOR][COLOR=#000000] [/COLOR]

[COLOR=#000000]**Missing Optional Dependencies**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]**-----------------------------**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FF5454]**error: 'python3-dbus.mainloop.qt' package is missing/incompatible **[/COLOR][COLOR=#000000] [/COLOR]

Total Errors: 3
Total Warnings: 1

Not an answer to your question but at least you have a reference check.

I fall back to an earlier OS when I have to print. One day I will sort it out.

[/FONT]

---

### Post by zkab on 2020-10-19
I upgraded to 20.10 ... so far the printer is working

---

### Post by ActionParsnip on 2020-10-19
[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)
Doesn't show a HP LaserJet Pro m402dne but does show a HP LaserJet Pro m402dn
Can't see their being a huge difference.

---

