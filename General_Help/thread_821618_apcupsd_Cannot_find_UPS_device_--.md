---
title: "apcupsd: Cannot find UPS device --"
date: 2008-06-07
forum: General Help
---

### Post by jmvidalvia on 2008-06-07
Hi!
I am trying to connect an UPS (iDialog / Riello) to my server.
I installed apcupsd, but it doesn't get any signal from the UPS.
As far as I understand, it seems it can not find the UPS.
Plase, find below some usefull information:


```

server:/dev# dmesg
usb 1-7: new low speed USB device using ohci_hcd and address 6
usb 1-7: configuration #1 chosen from 1 choice
cypress 1-7:1.0: HID->COM RS232 Adapter converter detected
usb 1-7: HID->COM RS232 Adapter converter now attached to ttyUSB0

```

```
server:/etc/apcupsd# cat /proc/bus/usb/devices

/...

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=03 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04b4 ProdID=5500 Rev= 0.00
S:  Manufacturer=Cypress Semiconductor
S:  Product=USB to Serial
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=cypress
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

```
server:/etc/apcupsd# cat apcupsd.conf | grep -v "#"
UPSCABLE usb
UPSTYPE usb
DEVICE /dev/ttyUSB0

LOCKFILE /var/lock
SCRIPTDIR /etc/apcupsd
PWRFAILDIR /etc/apcupsd
NOLOGINDIR /etc
ONBATTERYDELAY 6
BATTERYLEVEL 5
MINUTES 3
TIMEOUT 0
ANNOY 300
ANNOYDELAY 60
NOLOGON disable
KILLDELAY 0
NETSERVER on
NISIP 127.0.0.1
NISPORT 3551
EVENTSFILE /var/log/apcupsd.events
EVENTSFILEMAX 10
UPSCLASS standalone
UPSMODE disable
STATTIME 0
STATFILE /var/log/apcupsd.status
LOGSTATS off
DATATIME 0

```

```
server:/etc/apcupsd# tail -f /var/log/apcupsd.events
Sat Jun 07 17:40:35 CEST 2008  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Jun 07 17:40:35 CEST 2008  apcupsd error shutdown completed

```

I have no idea about next possible step...:(
Thanks so much!

---

### Post by strider1551 on 2008-06-07
I've successfully set up apcupsd to work with my own ups.  Unfortunately, mine is an actual APC brand unit, and I'm running Gentoo.  The [documentation]("http://gentoo-wiki.com/HOWTO_APCUPSD") in the Gentoo wiki might help you figure out what might be wrong.

You problem shouldn't have anything to do with your kernel configuration, since "cat /proc/bus/usb/devices" listed both the ups and a driver.

Are you sure that apcupsd works with your ups?  Their list of supported models is [here]("http://www.apcupsd.org/manual/Supported_UPSes_Cables.html").  You might be able to use [NUTs]("http://eu1.networkupstools.org/compat/stable.html") instead; it sounds like it can handle a generic ups.

Best of luck.  Sorry I don't have a good, simple answer.

---

### Post by wolfen69 on 2008-06-07
any UPS will work with ubuntu. they are platform independant. it's just that ubuntu will not be able to manage shutdown times and such. but your computer will stay on after a power outage.

---

### Post by jmvidalvia on 2008-06-08
Thank you very much all of you.
I will change my UPS by a new one supported by NUT.
Obviously my UPS is working, but I want it to connect to my Linux box so, if power supply fails for more than some few minutes, it can send me an e-mail and shut the box down.
Thanks!

---

