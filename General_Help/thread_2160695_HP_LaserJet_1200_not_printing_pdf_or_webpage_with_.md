---
title: "HP LaserJet 1200 not printing pdf or webpage with graphics"
date: 2013-07-07
forum: General Help
---

### Post by bjackfly on 2013-07-07
Hi, I am running ubuntu 13.04 and I am having issues with my HPLaserJet 1200 using the HPLib. 
 

It can print the test page or a text document, but pdf or a web page with graphics.. the lights blink like the print job is in progress but then it will just hang there forever. I have this printer hooked up via a usb hub I think it could be a connection issue. Can someone school me on how to fix this? I really appreciate it.

```
* /var/log/syslog
 
Jul  7 17:48:42 BigJackFly kernel: [13195.651395] usblp 2-1.1.1.1:1.0: usblp1: USB Bidirectional printer dev 9 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0317
Jul  7 17:48:42 BigJackFly logger: loading HP Device 002 009
Jul  7 17:49:11 BigJackFly udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1.1/2-1.1.1.1:1.0
Jul  7 17:49:11 BigJackFly udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1.1/2-1.1.1.1:1.0
Jul  7 17:49:11 BigJackFly udev-configure-printer: MFG:Hewlett-Packard MDL:HP LaserJet 1200 SERN:- serial:-
Jul  7 17:49:12 BigJackFly kernel: [13225.274605] usblp1: removed
Jul  7 17:49:12 BigJackFly kernel: [13225.277782] usblp 2-1.1.1.1:1.0: usblp1: USB Bidirectional printer dev 9 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0317
Jul  7 17:49:12 BigJackFly udev-configure-printer: URI matches without serial number: usb://HP/LaserJet%201200?serial=00CNBQ059066
Jul  7 17:49:12 BigJackFly udev-configure-printer: No serial number URI matches so using those without
Jul  7 17:49:12 BigJackFly udev-configure-printer: URI of detected printer: usb://HP/LaserJet%201200?serial=00CNBQ059066, normalized: laserjet 1200 serial 00cnbq059066
Jul  7 17:49:12 BigJackFly udev-configure-printer: URI of print queue: hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066, normalized: laserjet 1200 serial 00cnbq059066
Jul  7 17:49:12 BigJackFly udev-configure-printer: Queue ipp://localhost:631/printers/HP_LaserJet_1200 has matching device URI
Jul  7 17:56:24 BigJackFly kernel: [13656.834375] usblp1: removed
Jul  7 17:57:50 BigJackFly hp[31222]: io/hpmud/musb.c 1447: unable to write data hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066: 45 second io timeout
Jul  7 17:58:45 BigJackFly hp[31222]: io/hpmud/musb.c 1447: unable to write data hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066: 45 second io timeout

 * shows the output of hp-check -t and the distro of my linux.

Linux 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Saving output in log file: /home/bsamim/workspace/Callback/hp-check.log
HP Linux Imaging and Printing System (ver. 3.13.6)
Dependency/Version Check Utility ver. 15.1
Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
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
    MISSING - Missing Dependency or Permission or Plug-in
    INCOMPAT - Incompatible dependency-version or Plugin-version
---------------
| SYSTEM INFO |
---------------
 Kernel: 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 GNU/Linux
 Host: BigJackFly
 Proc: 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 GNU/Linux
 Distribution: ubuntu 13.04
 Bitness: 64 bit
-----------------------
| HPLIP CONFIGURATION |
-----------------------
HPLIP-Version: HPLIP 3.13.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro 13.04 version
Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.
[hplip]
version=3.13.6
[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.13.6
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
internal-tag=3.13.6
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
Plugins are not installed. Could not access file: No such file or directory
Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1372366201
pending_upgrade_time = 0
latest_available_version = 3.13.6
[settings]
systray_visible = 0
systray_messages = 0
[last_used]
device_uri = "hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066"
printer_name = HP_LaserJet_1200
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
date_time = 07/05/2013 17:33:35
version = 3.13.6
 <Package-name> <Package-Desc> <Required/Optional> <Min-Version> <Installed-Version> <Status> <Comment>
--------------------------
| External Dependencies |
--------------------------
 gs Ghostscript REQUIRED 7.05 9.07 OK -
 network Network-wget OPTIONAL - 1.14 OK -
 dbus DBus REQUIRED - 1.6.8 OK -
 scanimage Shell-Scanning OPTIONAL 1.0 1.0.23 OK -
 policykit Admin-Policy-framework OPTIONAL - 0.105 OK -
 xsane SANE-GUI OPTIONAL 0.9 0.998 OK -
 cups CUPS REQUIRED 1.1 1.6.2 OK 'CUPS Scheduler is running'
-------------------------
| General Dependencies |
-------------------------
 reportlab Python-PDF-Lib OPTIONAL 2.0 2.6 OK -
 libcrypto OpenSSL-Crypto-Lib REQUIRED - 1.0.1 OK -
 pil Python-Image-Lib OPTIONAL - 1.1.7 OK -
 pyqt4-dbus PyQt4-DBUS REQUIRED 4.0 4.10 OK -
 libjpeg JPEG-Lib REQUIRED - - OK -
 libpthread POSIX-Threads-Lib REQUIRED - 2.17 OK -
 python-dbus Python-DBUS REQUIRED 0.80.0 1.1.1 OK -
 python-devel Python-SDK REQUIRED 2.2 2.7.4 OK -
 pyqt4 Python-Qt4 REQUIRED 4.0 4.10 OK -
 cups-devel CUPS-SDK REQUIRED - 1.6.2 OK -
 sane-devel SANE-SDK REQUIRED - 1.0.23 OK -
 libusb USB-Lib REQUIRED - 1.0 OK -
 sane Scan-Lib REQUIRED - 1.0.23 OK -
 cups-image CUPS-Image-Lib REQUIRED - 1.6.2 OK -
 libnetsnmp-devel SNMP-Networking-SDK REQUIRED 5.0.9 5.4.3 OK -
 python-xml Python-XML-Lib REQUIRED - 2.1.0 OK -
 python-notify Desktop-notifications OPTIONAL - - OK -
------------------------------
| Compile Time Dependencies |
------------------------------
 gcc gcc-Compiler REQUIRED - 4.7.3 OK -
 libtool Build-tools REQUIRED - 2.4.2 OK -
 make GNU-Build-tools REQUIRED 3.0 3.81 OK -
----------------------
| Python Extentions |
----------------------
 cupsext CUPS-Extension REQUIRED - 3.13.6 OK -
 pcardext PhotoCard-Extension REQUIRED - 3.13.6 OK -
 hpmudext IO-Extension REQUIRED - 3.13.6 OK -
-----------------------
| Scan Configuration |
-----------------------
 hpaio HPLIP-SANE-Backend REQUIRED - 3.13.6 OK 'hpaio found in /etc/sane.d/dll.conf'
 scanext Scan-SANE-Extension REQUIRED - 3.13.6 OK -
------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------
No Scanner found.
--------------------------
| DISCOVERED USB DEVICES |
--------------------------
  Device URI Model
  -------------------------------- ----------------
  hp:/usb/HP_LaserJet_1200?serial= HP LaserJet 1200
  00CNBQ059066
---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------
HP_LaserJet_1200
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066
PPD: /etc/cups/ppd/HP_LaserJet_1200.ppd
PPD Description: HP LaserJet 1200 Postscript (recommended)
Printer status: printer HP_LaserJet_1200 is idle. enabled since Fri 05 Jul 2013 05:05:04 PM CDT
 ready to print
Communication status: Good
--------------
| PERMISSION |
--------------
groups user-groups Required - - OK bsamim adm lp cdrom sudo dip plugdev lpadmin sambashare
USB HP_LaserJet_1200 Required - - OK Node:'/dev/bus/usb/002/011' Perm:' root lp rw- rw- rw- rw- ---'
No errors or warnings.
```
D

---

### Post by bjackfly on 2013-07-07
Hi, I am pretty new to Ubuntu but have researched this issue heavily and still cannot find a solution. I have installed the hplip and have the printer connected to a usb port. If I select some text on a web page and say print selection it has no problems. It can print the test page, it can print a document from Libre Office but if I print out a web page with graphics or a pdf document it will not work. It will flash the light like the printer is ready to print the job but then it will just hang and eventually give a timeout. I thought it could be a usb thing but I have no idea. Can you please give me some advice on how to fix this?  The syslog will show timeout and eventually the printer will give a system page with a timeout.  The light will blink like it's processing the job it just will never finish.  Afterwards I will have to kill the **lp** command that is running or I see " imuxsock begins to drop messages from pid 26271 due to rate-limiting " keep printing out in the systems log. I am kind of at a loss at this point.. Any help is greatly appreciated.

```
/var/log/syslog

Jul  7 20:13:47 BigJackFly hp[1529]: prnt/backend/hp.c 371: read new pjl status: 10001
Jul  7 20:14:40 BigJackFly hp[1529]: io/hpmud/musb.c 1447: unable to write data hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066: 45 second io timeout


[B]
hp-check -t [/B]

 *Saving output in log file: /var/log/hp-check.log

HP Linux Imaging and Printing System (ver. 3.13.6)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the   
proper dependencies are installed to successfully compile HPLIP.                                                                                
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP       
supplied tarball has the proper dependencies installed to successfully run.                                                                     
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time     
dependencies).                                                                                                                                  

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

 Kernel: 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 GNU/Linux
 Host: BigJackFly
 Proc: 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 GNU/Linux
 Distribution: ubuntu 13.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.13.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  13.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.13.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.13.6
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
internal-tag=3.13.6
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
[plugin]
installed = 1
eula = 1
version = 3.13.6



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1372366201
pending_upgrade_time = 0
latest_available_version = 3.13.6

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066"
printer_name = HP_LaserJet_1200
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
date_time = 07/07/2013 20:09:18
version = 3.13.6


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            9.07            OK         -
 network              Network-wget              OPTIONAL        -               1.14            OK         -
 dbus                 DBus                      REQUIRED        -               1.6.8           OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.6.2           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.6             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10            OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.1.1           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.4           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10            OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.6.2           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.6.2           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.7.3           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.13.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.13.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.13.6          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.13.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.13.6          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                    Model                       
  --------------------------------------------  ----------------------------
  hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066  HP LaserJet 1200            

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


HP_LaserJet_1200
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1200?serial=00CNBQ059066
PPD: /etc/cups/ppd/HP_LaserJet_1200.ppd
PPD Description: HP LaserJet 1200 Postscript (recommended)
Printer status: printer HP_LaserJet_1200 is idle.  enabled since Sun 07 Jul 2013 07:46:09 PM CDT
Communication status: Good


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       bsamim adm lp cdrom sudo dip plugdev lpadmin sambashare

USB             HP_LaserJet_1200               Required        -        -        OK       Node:'/dev/bus/usb/002/030' Perm:'  root  lp rw- rw- rw- rw- ---'
No errors or warnings.
```

Done.

---

### Post by cariboo on 2013-07-07
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by bjackfly on 2013-07-08
It wouldn't let me delete the first post, also I tried to edit the subject line which was slightly misleading to the problem but it didn't let me.

---

### Post by bjackfly on 2013-07-09
changed the driver using cups 127.0.0.1:631  go to Administration tab and changed the driver to be the following and I have no issues at all now:

*HP LaserJet 1200 - CUPS+Gutenprint v5.2.9

---

### Post by VinDSL on 2013-07-09
> **bjackfly said:**
> changed the driver using cups 127.0.0.1:631
Another handy way is open a terminal, and...

```
system-config-printer
```

---

