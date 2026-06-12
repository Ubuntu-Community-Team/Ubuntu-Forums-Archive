---
title: "[ubuntu 15.10] HP Officejet 6700 printing problem"
date: 2015-12-07
forum: General Help
---

### Post by franz.patz on 2015-12-07
Dear Community,

I have searched in the forum and found a lot of people somehow struggling with HP printers, but none of the posts helped me to get things running at my site so far and since I am a Linux beginner, all I can do at this point is trying things blindly - so I hope that someone can guide me through some "debugging".

I have a HP Officejet 6700 Premium printer, it is connected to the network via WLAN and I can print and scan when using the Windows OS.
Now I installed the hp drivers, but If I try to print something nothing happens at the printer although on the desktop, I get the message: "HPLIP Desvice Status: Print Job has completed"
When I look into the print status it says "held", and when I do a right click --> view attributes, the "job-state-reason" is "resources-are-not-ready".

When I use the graphical way and go into the HP Device Manager and click on the printer  and "view printer and device information", it pops-up the error "Unable to open device hp:/net/Officejet_6700?ip=10.0.0.59", which is kind of weird because the printer has a "local" ip adress in the range 192.168.0.x" and nothing like "10.0.0x" ? Then, also in the status, the HP Device manager shows up a generic, and not further specified "communication error".


The printer is turned on and I can ping it. Now, when I run hp-check, it produces a huge amount of output, including some messages about missing packages (I just show the red-lined errors below).

error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 error: xsane         xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             -               MISSING    'xsane needs to be installed'
 error: dbus          DBus - Message bus system                                    REQUIRED        -               1.10.0          MISSING    'DBUS may not be installed or not running'

 error: cups-devel    CUPS devel- Common Unix Printing System development files    REQUIRED        -               -               MISSING    'cups-devel needs to be installed'

 error: python3-devel Python devel - Python development files                      REQUIRED        2.2             3.4.3           MISSING    'python3-devel needs to be installed'
 error: libnetsnmp-devel libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           -               MISSING    'libnetsnmp-devel needs to be installed'

 error: libcrypto     libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           MISSING    'libcrypto needs to be installed'

 error: libjpeg       libjpeg - JPEG library                                       REQUIRED        -               -               MISSING    'libjpeg needs to be installed'
 error: sane-devel    SANE - Scanning library development files                    REQUIRED        -               -               MISSING    'sane-devel needs to be installed'
 error: cups-image    CUPS image - CUPS image development files                    REQUIRED        -               -               MISSING    'cups-image needs to be installed'

 error: libtool       libtool - Library building support services                  REQUIRED        -               -               MISSING    'libtool needs to be installed'

error: Unable to communicate with device (code=12): hp:/net/Officejet_6700?ip=10.0.0.59
error: unable to open channel
error: Communication status: Failed

Printer status: printer Officejet_6700_fax is idle.  enabled since Don 29 Okt 2015 00:03:03 CET
error: Incorrect PPD file for fax queue 'Officejet_6700_fax'. Fax queues must use 'HP-Fax-hplip.ppd'.
error: Unable to communicate with device (code=12): hpfax:/net/Officejet_6700?ip=10.0.0.59
error: unable to open channel
error: Communication status: Failed


Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing/incompatible 
error: 'libdbus-1-dev' package is missing/incompatible 
error: 'libcups2-dev' package is missing/incompatible 
error: 'cups-bsd' package is missing/incompatible 
error: 'cups-client' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 
error: 'libsnmp-dev' package is missing/incompatible 
error: 'snmp-mibs-downloader' package is missing/incompatible 
error: 'openssl' package is missing/incompatible 
error: 'libjpeg-dev' package is missing/incompatible 
error: 'libsane-dev' package is missing/incompatible 
error: 'libcupsimage2-dev' package is missing/incompatible 
error: 'libtool' package is missing/incompatible 
error: 'libtool-bin' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'xsane' package is missing/incompatible 



Now I tried the obvious thing of installing some of the missing dependencies listed above, but the apt-get tells me that there is nothing to update (maybe it's "just" a version conflict, but how to resolve this?)
Finally, some people in the forum talked about running hp-doctor, which I also did, and which tells me the following:


HP Linux Imaging and Printing System (ver. 3.15.7)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-15 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Checking for Deprecated items....
error: This distro (i.e ubuntu  15.10) is either deprecated or not yet supported.
The diagnosis is limited on unsupported platforms. Do you want to continue?(y=yes*, n=no):


So, after over an hour of just wanting to print a single page of text, I am kind of lost in the world of linux and could need some help ;-)

Thanks a lot and best regards,
Franz

---

### Post by Ricardo_Velasco on 2015-12-07
Greeting:

Forgive me for not giving this answer as objective and may not help much , but ..

Look at the console messages:

> error: 'libcups2' package is missing/**incompatible **

error: 'libdbus-1-dev' package is missing/[B]incompatible 
[/B]
error: 'libcups2-dev' package is missing/**incompatible **

error: 'cups-bsd' package is missing/**incompatible** 

error: 'cups-client' package is missing/**incompatible** 

error: 'python3-dev' package is missing/**incompatible **

error: 'libsnmp-dev' package is missing/**incompatible **

error: 'snmp-mibs-downloader' package is missing/**incompatible **

error: 'openssl' package is missing/**incompatible** 

error: 'libjpeg-dev' package is missing/**incompatible **

error: 'libsane-dev' package is missing/**incompatible** 

error: 'libcupsimage2-dev' package is missing/**incompatible** 

error: 'libtool' package is missing/**incompatible** 

error: 'libtool-bin' package is missing/**incompatible**



> Checking for Deprecated items....

**error: This distro (i.e ubuntu  15.10) is either deprecated or not yet supported.**

The diagnosis is limited on unsupported platforms. Do you want to continue?(y=yes*, n=no):



Unfortunately this distribution is not supported by the printer manufacturer .

I always recommend not installing very recent distributions such incompatibility problems :(

I recommend installing an older version such as Ubuntu 12.04 LTS or Ubuntu 14.04 LTS

Sorry

---

### Post by Geoffrey_Arndt on 2015-12-08
The HP Office Jet 6700 is supported just fine in Ubuntu 15.10 ([http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html)]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6700.html")

Just need to know how to get started on the right path.    

First, some general concepts:

>   99.5% of all HP Printers are supported very well in Linux.
>   The base install of most distros including Ubuntu already contain all the driver modules (normally merged into the kernel) to run these printers.   Unless the printer is brand new (< 6 months) - - no special drivers "usually" need to be installed.
>   Never go and search out drivers and install them UNTIL or UNLESS you've tried to add the printer via the gui process (system settings>printer) and adding the printer (the printer _should always be connected via USB cable_ at first boot and when doing the initial install (re the discovery process).
>   If you've jumped ahead and installed printers via the same kind of process you use with Windows (finding the drivers via the web at multiple trusted/untrusted sites) - - - that leads to problems.    Often it means these installed drivers need to be fully purged and then reinstalled via the automatic discover process described in general above.

So, to provide more info - can you describe in detail how you've installed the drivers including where you've obtained them from.

---

### Post by franz.patz on 2015-12-08
First of all, thank you for the replies!

Oh well, yes I am afraid that I have "jumped ahead and installed printer drivers from HP", to be more specific: As far as I remember (it's been a few weeks), I just went to 

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) ,

selected the correct version, downloaded HPLIP and installed it as proposed. I did not think of the possibility, that a vendor-provided driver that is available for the right version of the used Linux distribution could possibly brake things... :(

Thanks!

EDIT: After running hp-doctor once again and manually installed all packages it complained about as missing/incompatible, the following errors remain as output of the utility:
error: Unable to communicate with device (code=12): hpfax:/net/Officejet_6700?ip=10.0.0.59
error: unable to open channel
error: Communication status: Failed

Checking for Printer Status....
error: 'Officejet_6700' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor
error: 'Officejet_6700_fax' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor

EDIT2:
Ok, so I forgot the commandline stuff and removed the two detected Printers (printer and fax from the HPLIP Device Manager). Then I went into the CUPS webinterface via
[http://localhost:631](http://localhost:631)
and added the printer there

Now, looking into the HPLIP Device Manager it says that there is no HPLIP device installed but the CUPS webinterface says the printer is ok and idle. And woooosh, printing seems to work...!
Although I haven't learned much from this approach, I am glad it's working and thank all the people for providing tools like this webinterface that obviously 'automatically' configure stuff the right way  :)

---

