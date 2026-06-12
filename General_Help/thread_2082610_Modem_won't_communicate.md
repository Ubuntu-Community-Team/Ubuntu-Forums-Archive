---
title: "Modem won't communicate"
date: 2012-11-10
forum: General Help
---

### Post by RogerDavis on 2012-11-10
Modem will not respond in Efax-gtk or in Minicom after initialization. 

This modem works fine in Windoze, SAME machine, just switched to Ubuntu 12.04 drive by mechanical switch.  I can go back and forth, always works in Windoze, never in Ubuntu.

Modem will attempt to answer an incoming call, but can't be sure about function since I don't have another modem to call with.
 
IN MINICOM :
Welcome to minicom 2.5
OPTIONS: I18n 
Compiled on May  2 2011, 10:05:24.
Port /dev/ttyS4
Press CTRL-A Z for help on special keys
Nothing further will be shown, no matter what keyboard input, etc. - except it will respond to CTL-A and Z, which are not modem responses         

IN EFAX-GTK :
efax-0.9a: 21:27:23 opened /dev/ttyS4
)Then try to send and wait 5 minutes - no result, so press "Stop")
*** Stopping send/receive session ***
efax-0.9a: 21:27:46 failed page /home/roger/Documents/Libre Office/Saddleback Labs Request.pdf.001                                                 
                                            
MODEM INFO :

At ttyS4

*-pci
description: PCI bridge
product: Integrated Technology Express, Inc.
vendor: Integrated Technology Express, Inc.
physical id: 0 bus info: pci@0000:03:00.0
version: 30 width: 32 bits clock: 33MHz
capabilities: pci pm subtractive_decode bus_master cap_list
resources: ioport:d000(size=4096)
memory:f7d00000-f7dfffff

*-communication
description: Serial controller product: 56K FaxModem Model 5610
vendor: 3Com Corp, Modem Division
physical id: 1 bus info: pci@0000:04:01.0
version: 01 width: 32 bits clock: 33MHz
capabilities: pm 16550 cap_list
configuration: driver=serial latency=0
resources: irq:17 ioport:d000(size=8)

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
Sorry, NO MODEM WAS DETECTED! Is it in use by another program? - (my caps)
Did you configure it properly with setserial?

OK, so Ubuntu finds the modem, but doesn't find it !?!?!? Which is correct ?!?

I am a member of dialout group and all others I could think of that might affect this

I'm almost ready to believe it's a kernel problem, except not by intent. I can't imagine anyone would intentionally screw that up thinking it's best for the world...

I'm NOT trying to connect to an ISP right now, I want to use it with eFax-GTK.

It worked on 12.04 before one of the later updates which included Ubuntu segments as well as others. Then it just quit...

---

### Post by ummelum on 2012-12-03
if this isn't solved yet:

[http://ubuntuforums.org/showthread.php?p=12386577](http://ubuntuforums.org/showthread.php?p=12386577)
[http://ubuntuforums.org/showthread.php?t=2089911](http://ubuntuforums.org/showthread.php?t=2089911)
[http://ubuntuforums.org/showthread.php?p=12386595](http://ubuntuforums.org/showthread.php?p=12386595)

other people have similar problems...

---

### Post by ummelum on 2012-12-06
***can someone clue me in why this isn't working as it should? i find it hard to believe i'm the only ubuntu-user that needs a working serial port.***

---

### Post by ummelum on 2012-12-07
silent bump, and link to the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)

---

