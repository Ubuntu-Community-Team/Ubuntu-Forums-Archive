---
title: "pppconfig"
date: 2007-01-07
forum: General Help
---

### Post by cssutto on 2007-01-07
I am installing from scratch on a new box and I am having the usual problems with dialing.

I am using a KPC 650 card modem and it requires two commands to get it going:

 sudo modprobe usbserial vendor=0xc88 product=0x17da

wvdialconf /etc/wvdial.conf

Then either wvdial or pon alltel will start the dialer.

I prefer pon alltel.

I have properly configured pppconfig.

My problem is that this must be done on every boot.

Since this is a laptop that travels, it gets booted 3 or 4 times a day.  Plus the boots required when I dual boot into windoze.

So this is a pain.

I tried putting  sudo modprobe usbserial vendor=0xc88 product=0x17da in /etc/modules but that did not cure the problem.

A suggestion would be appreciated.

CSSJR

---

### Post by koenn on 2007-01-07
create a file : /etc/init.d/dialup

in that file, put the commands you want to execute (don't put any sudo there)
```
modprobe usbserial vendor=0xc88 product=0x17da
wvdialconf /etc/wvdial.conf
pon alltel
```

make it executable 
```
chmod 770 /etc/init.d/dialup
```

create links in the 'startup' directories
```
update-rc.d dialup defaults 99
```

see if it works.

---

### Post by cssutto on 2007-01-08
That works great!

Thanks.

The only change I made was I left out the pon alltel command because I prefer to start it when I am ready.

Thanks.

CSSJR

---

### Post by koenn on 2007-01-08
makes sense. 

have fun.

---

### Post by rushkoff on 2007-03-26
I've got the same card, and it doesn't seem so easy for me.
I tried your first line, but the second line yields:

rushkoff@rushkoff-laptop:~$ wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: Kyocera Wireless Corp.
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- OK
ttyUSB0<*1>: Max speed is 460800; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp5527': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


Which I guess means, what, that I don't have wvdial installed - or that I don't have permission to do anything to it?

---

### Post by koenn on 2007-03-26
> **rushkoff said:**
> 
Which I guess means, what, that I don't have wvdial installed - or that I don't have permission to do anything to it?
It probably means you have insufficient permissions to modify wvdial.conf
try running those commands with "sudo" eg
```
sudo wvdialconf /etc/wvdial.conf
```

sudo is not mentioned in the script below because the script itself runs with root privilegues at startup.

---

