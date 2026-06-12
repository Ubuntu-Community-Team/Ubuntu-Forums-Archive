---
title: "RPM package in Ubuntu"
date: 2012-11-18
forum: General Help
---

### Post by RogerDavis on 2012-11-18
It is possible to install an RPM (Red Hat Package Manager) package in Ubuntu?  

Specifically, this one - LNUX_3ComMdm-1.0-1.i386.rpm.  
===================================
Red Hat Package Manager
USRobotics Corporation is pleased to provide the following Red Hat Package Manager (.rpm) support file. This RPM package has been tested under Red Hat Linux 6.0 and higher. It should also work with other Linux distributions supporting the RPM utility.

Install the RPM file by entering the rpm -i 3ComMdm-1.0-1.i386.rpm command at the command prompt.

This file can also be used as a basis to write your own script for UNIX/LINUX hybrids. If you make your own scripts for a hybrid, it would be appreciated if you could send this script to USRobotics so that we may post it so that others may benefit as well.

This is a BETA test file which is not supported by USRobotics.

LNUX_3ComMdm-1.0-1.i386.rpm	7987 bytes 	07/27/2001

===============================
See [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c)

---

### Post by latinlightning on 2012-11-18
You can try alien to convert the RPM into a deb.

Here's the man page for alien: [http://manpages.ubuntu.com/manpages/gutsy/man1/alien.1p.html](http://manpages.ubuntu.com/manpages/gutsy/man1/alien.1p.html) 

I used it when I downloaded and installed the latest version of Nmap from source and it worked just fine.

Here's a link on how-to use alien: [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by oldos2er on 2012-11-18
> **RogerDavis said:**
> 
LNUX_3ComMdm-1.0-1.i386.rpm	7987 bytes 	07/27/2001


I'd be surprised if you got something this old to work. Can you explain what you're wanting to do?

---

### Post by idoitprone on 2012-11-18
> **oldos2er said:**
> I'd be surprised if you got something this old to work. Can you explain what you're wanting to do?


Do not underestimate red hat linux. It is probably more stable than debian stable

---

### Post by RogerDavis on 2012-11-19
OK, here is why I might want to try this driver.  I am concerned the Ubuntu kernel may have abandoned this type of modem (internal, serial, full processor type).  Because it's internal, it works off of ttyS4, different from other serial ports.  Some supposedly knowledgeable people simply don't even know about this type of modem.  If they are working on the kernel, I can just see them thinking "Who needs this code, it doesn't do anything I know about...) If this is true, maybe someone in the know can at least let me know so I don't make myself any more crazy than this has already made me.

Anyway, full details below:
================================================= 
Ubuntu 12.04 finds but ignores USR internal serial modem with built in comm port, full hardware included.  ( This is basically an internal US Robotics Sportster modem, NOT a Winmodem.  See   [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c) for full info.

Minicom and Efax-gtk will not work. Both appear to initialize (can't be sure, just software seems satisfied, no error codes), but no further function, no response to modem commands given, etc.  This appears to be a problem with Ubuntu communicating the the modem at the lowest level.

I'm NOT trying to connect to an ISP right now, I just want to use it with eFax-GTK, and am using Minicom also for testing.

This exact same modem and computer worked together very well until recently. There had been several updates, including to Ubuntu before it just quit working.

This modem works fine in Windoze, SAME machine, just switch to Ubuntu 12.04 drive by mechanical switch. I can go back and forth, always works in Windoze, never in Ubuntu.  When I first installed 12.04, it worked fine, simply quit working after some updates.

Modem will attempt to answer an incoming call, but can't be sure about function since I don't have another modem to call with.

I have come to the conclusion that there is likely a problem within the updated Ubuntu that prevents proper basic communication between the OS and modem.  I hope I am proven wrong and there is a way to fix this.

IN MINICOM :
Welcome to minicom 2.5
OPTIONS: I18n
Compiled on May 2 2011, 10:05:24.
Port /dev/ttyS4
Press CTRL-A Z for help on special keys
( Nothing further will be shown besides local echo, no matter what keyboard input, etc. - except it will respond to CTL-A and Z, which are not modem responses )

IN EFAX-GTK :
efax-0.9a: 21:27:23 opened /dev/ttyS4
( Then try to send and wait 5 minutes - no result, so press "Stop" )
*** Stopping send/receive session ***
efax-0.9a: 21:27:46 failed page /home/roger/Documents/Libre Office/Saddleback Labs Request.pdf.001

I am a member of dialout and dip.

Modem info:  (FOUND MODEM)
description: Serial controller product: 56K FaxModem Model 5610
vendor: 3Com Corp, Modem Division
physical id: 1 bus info: pci@0000:04:01.0
version: 01 width: 32 bits clock: 33MHz
capabilities: pm 16550 cap_list
configuration: driver=serial latency=0
resources: irq:17 ioport:d000(size=8 )

roger@roger-desktop:~$ sudo wvdialconf
[sudo] password for roger:
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0 S1 S2 S3
ttyS4<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS4<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS4<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S5 S6 S7 S8
Modem Port Scan<*1>: S9 S10 S11 S12 S13 S14 S15 S16
Modem Port Scan<*1>: S17 S18 S19 S20 S21 S22 S23 S24
Modem Port Scan<*1>: S25 S26 S27 S28 S29 S30 S31
Sorry, NO MODEM WAS DETECTED! Is it in use by another program? - ( my caps )
Did you configure it properly with setserial?

( OK, so Ubuntu finds the modem, but doesn't find it !?!?!? )

( This is basically an internal US Robotics Sportster modem, NOT a Winmodem.  See   [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c) for full info.

Modem is at ttyS4 (has it’s own built-in serial port)

roger@roger-desktop:~$ cat /var/log/syslog | grep modem
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> ModemManager (version 0.5.2.0) starting...
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin SimTech
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin MotoC
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Ericsson MBM
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin ZTE
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Linktop
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin AnyData
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Option High-Speed
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Wavecom
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Sierra
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Samsung
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Novatel
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Generic
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Huawei
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Longcheer
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin X22X
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Nokia
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Option
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> Loaded plugin Gobi
Nov 9 13:26:47 roger-desktop modem-manager[919]: <info> (ttyS4) opening serial port...
Nov 9 13:26:47 roger-desktop NetworkManager[932]: <info> modem-manager is now available
Nov 9 13:26:59 roger-desktop modem-manager[919]: <info> (ttyS4) closing serial port...
Nov 9 13:26:59 roger-desktop modem-manager[919]: <info> (ttyS4) serial port closed
Nov 9 13:26:59 roger-desktop modem-manager[919]: <info> (ttyS4) opening serial port...
Nov 9 13:27:05 roger-desktop modem-manager[919]: <info> (ttyS4) closing serial port...
Nov 9 13:27:05 roger-desktop modem-manager[919]: <info> (ttyS4) serial port closed
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> ModemManager (version 0.5.2.0) starting...
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin SimTech
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin MotoC
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Ericsson MBM
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin ZTE
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Linktop
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin AnyData
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Option High-Speed
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Wavecom
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Sierra
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Samsung
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Novatel
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Generic
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Huawei
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Longcheer
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin X22X
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Nokia
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Option
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> Loaded plugin Gobi
Nov 9 17:32:07 roger-desktop modem-manager[934]: <info> (ttyS4) opening serial port...
Nov 9 17:32:07 roger-desktop NetworkManager[943]: <info> modem-manager is now available
Nov 9 17:32:19 roger-desktop modem-manager[934]: <info> (ttyS4) closing serial port...
Nov 9 17:32:19 roger-desktop modem-manager[934]: <info> (ttyS4) serial port closed
Nov 9 17:32:19 roger-desktop modem-manager[934]: <info> (ttyS4) opening serial port...
Nov 9 17:32:25 roger-desktop modem-manager[934]: <info> (ttyS4) closing serial port...
Nov 9 17:32:25 roger-desktop modem-manager[934]: <info> (ttyS4) serial port closed
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> ModemManager (version 0.5.2.0) starting...
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin SimTech
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin MotoC
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Ericsson MBM
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin ZTE
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Linktop
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin AnyData
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Option High-Speed
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Wavecom
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Sierra
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Samsung
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Novatel
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Generic
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Huawei
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Longcheer
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin X22X
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Nokia
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Option
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> Loaded plugin Gobi
Nov 9 17:41:31 roger-desktop modem-manager[932]: <info> (ttyS4) opening serial port...
Nov 9 17:41:31 roger-desktop NetworkManager[944]: <info> modem-manager is now available
Nov 9 17:41:43 roger-desktop modem-manager[932]: <info> (ttyS4) closing serial port...
Nov 9 17:41:43 roger-desktop modem-manager[932]: <info> (ttyS4) serial port closed
Nov 9 17:41:43 roger-desktop modem-manager[932]: <info> (ttyS4) opening serial port...
Nov 9 17:41:49 roger-desktop modem-manager[932]: <info> (ttyS4) closing serial port...
Nov 9 17:41:49 roger-desktop modem-manager[932]: <info> (ttyS4) serial port closed
Nov 10 00:39:36 roger-desktop AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Nov 10 00:39:41 roger-desktop AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov 10 00:42:07 roger-desktop AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s'))'
Nov 10 00:42:08 roger-desktop AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
roger@roger-desktop:~$

( I note I don't see US Robotics or 3Com Corp in the above list, but I think the Generic info should work with it ? )

I have come to the conclusion that there is very likely a problem within the updated Ubuntu that prevents proper  communication with this modem which has it’s own built-in serial port.  The above Ubuntu confusion about detected, then not detected seems to support that. I have over 50 man-hours in work trying to solve this problem. I have some concerns that someone made an "Imperial" decision that no one uses modems any more, particularly internal serial modems, and left out the needed code, much like as was done to floppy drives.

However, I hope I am wrong, and there is a way to fix this. Maybe one of the Ubuntu updates simply overwrote some "modem" or serial port code?  

Conflict with Ubuntu One?  

Any other ideas?

---

### Post by Zill on 2012-11-20
RogerDavis:  It is many years since I have used dial-up modems so cannot really recall many of the "wrinkles" need to get the things working!

However, the following thread gives a couple of tips that may help you with configuring the USR5610C:
[LIST][*][U S Robotics modem not detected by Gnome PPP in Ubuntu 12.04 LTS]("http://www.linuxquestions.org/questions/ubuntu-63/u-s-robotics-modem-not-detected-by-gnome-ppp-in-ubuntu-12-04-lts-4175418245/")[/LIST]
Specifically, make sure /etc/group gives you permission for modems and fax and try the following ownership modification:
```
chown root:users /dev/ttyS4
```
Good luck!

---

### Post by RogerDavis on 2012-11-20
I had already found this one ( [http://www.linuxquestions.org/questions/ubuntu-63/u-s-robotics-modem-not-detected-by-gnome-ppp-in-ubuntu-12-04-lts-4175418245/](http://www.linuxquestions.org/questions/ubuntu-63/u-s-robotics-modem-not-detected-by-gnome-ppp-in-ubuntu-12-04-lts-4175418245/) ).  There are several problems relating to the correct parameters.
1) I'm not wanting to connect to the internet, just to get the modem to respond to direct commands
2) This is not a USB modem as one responder mentions.
3) This is also one of the incorrect responders - "However, ttS4 sounds unlikely if this modem was working before. It needs to be a number 0 through 3 (counting starts at 0)."  This responder does not know that a controller based modem has it's own serial port at ttyS4.
4) At the time that this was written, my modem was working just fine in 12.04, the "upgrades" that may have killed it occurred only about two or three months ago.
5) I tried the "chown root:users /dev/ttyS4" at the time I found it... no help.

---

