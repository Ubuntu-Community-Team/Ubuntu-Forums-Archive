---
title: "hplip not finding wireless printer"
date: 2016-11-07
forum: General Help
---

### Post by yazdzik-k on 2016-11-07
Linux xxxxxxx 4.8.0-26-generic #28-Ubuntu SMP Tue Oct 18 14:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Dear friends,

obviously,  ubuntu 16.10
hplip from hp,  3.16.10

**hidpi screen!!!**

all updates to ubuntu from 7 nov, 15:54

issue -

since hplip 3.16.7 from repos did not work due to inability of qt.x(no idea which) to allow resolution compatible with unity tray,  and rendering,  for all intents and purposes, hplip worthless,  following forum advice, I installed the current version.

(side note - there should be a way to force qt 5.6 builds when installing things from apt ;) )

Now, everything works except that device manager does not recognise wireless printer.

a:  printer is seen on network in router
b: printer works on same laptop in windows
v: printer worked in 15.10 ubuntu
d. printer works from all other devices other than this laptop running ubuntu 16.10

add devices does not work from gui,  but hp-setup runs,  as expected,  simply will not recognise printer, which I suspect is due to the same missing module that does not allow gui to call setup.



suggestions?

(I had thought of trying to reinstall hplip 3.16.7 and manually adding ptqt modules,  but this seems to be counterintuitive - also,  as much as a six hour procedure pains me,  I could completely reinstall ubuntu and try again - reverting to  hplip 3.16.7 from apt-get is impossible due to deps)

best,
m

apologies but attach text filed failt first time

xxx:~$ sudo hp-check
Saving output in log file: /home/xxxxx/hp-check.log


HP Linux Imaging and Printing System (ver. 3.16.10)
Dependency/Version Check Utility ver. 15.1


Copyright (c) 2001-15 HP Development Company, LP
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


 
---------------
| SYSTEM INFO |
---------------


 Kernel: 4.8.0-26-generic #28-Ubuntu SMP Tue Oct 18 14:39:52 UTC 2016 GNU/Linux
 Host: deblap2
 Proc: 4.8.0-26-generic #28-Ubuntu SMP Tue Oct 18 14:39:52 UTC 2016 GNU/Linux
 Distribution: 12 16.10
 Bitness: 64 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.16.10
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.10 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.16.10


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.16.10
html=/usr/share/doc/hplip-3.16.10
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
internal-tag=3.16.10
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
apparmor_build=yes




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1478532588
pending_upgrade_time = 0
latest_available_version = 3.16.5


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hpfax:/usb/Officejet_4630_series?serial=CN56P690T705Y0"
printer_name = 
working_dir = .


[commands]
scan = /usr/bin/xsane -V %SANE_URI%


[refresh]
rate = 30
enable = true
type = 1


[polling]
enable = false
interval = 5
device_list = 


[fax]
voice_phone = 
email_address = 


[installation]
date_time = 11/07/2016 11:15:16
version = 3.16.10




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------
| COMPILEDEP |
--------------


 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               6.2.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -


------------------------
| General Dependencies |
------------------------


 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.2.0           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.11.4          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.24            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.12          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.0           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.4           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.0           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.12          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -


----------------------
| Scan Configuration |
----------------------


 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.10         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.10         OK         'hpaio found in /etc/sane.d/dll.conf'


-------------------------
| External Dependencies |
-------------------------


 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.19            OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.0           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.18            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.10         OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -


---------------------
| Python Extentions |
---------------------


 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.10         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.10         OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/net/officejet_4630_series?ip=192.168.0.13&queue=false' is a Hewlett-Packard officejet_4630_series all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


No devices found.


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
Officejet_4630
--------------
Type: Printer
Device URI: hp:/usb/Officejet_4630_series?serial=CN56P690T705Y0
PPD: /etc/cups/ppd/Officejet_4630.ppd
PPD Description: HP Officejet 4630 Series, hpcups 3.16.10
Printer status: printer Officejet_4630 disabled since Mon 07 Nov 2016 09:25:25 AM EST - Unplugged or turned off
error: Unable to communicate with device (code=12): hp:/usb/Officejet_4630_series?serial=CN56P690T705Y0
error: Device not found
error: Communication status: Failed


Officejet_4630_fax
------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_4630_series?serial=CN56P690T705Y0
PPD: /etc/cups/ppd/Officejet_4630_fax.ppd
PPD Description: HP Fax4 hpcups
Printer status: printer Officejet_4630_fax disabled since Mon 07 Nov 2016 09:25:25 AM ESUnplugged or turned off
error: Unable to communicate with device (code=12): hpfax:/usb/Officejet_4630_series?serial=CN56P690T705Y0
error: Device not found
error: Communication status: Failed




--------------
| PERMISSION |
--------------


 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
None


Missing Optional Dependencies
-----------------------------
None




Total Errors: 2
Total Warnings: 0




Done.

---

