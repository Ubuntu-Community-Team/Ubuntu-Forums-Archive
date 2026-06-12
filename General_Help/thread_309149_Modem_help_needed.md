---
title: "Modem help needed"
date: 2006-11-29
forum: General Help
---

### Post by DougieFresh4U on 2006-11-29
Two of my machines have modems. I have run scan modem on both. Also have read How-To for Smarlink and PCtel modems, I guess I am thick in the head as I still cannot get either one recognized and not sure how to configure. I guess I need a little "Hand Holding" on this. I tried wvdial on this machine and get ::dougie@DougiesToyBox:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
dougie@DougiesToyBox:~$

---

### Post by DougieFresh4U on 2006-11-29
would posting output from scanmodem help?

---

### Post by DougieFresh4U on 2006-11-29
**unbelievable!!**

---

### Post by DougieFresh4U on 2006-11-29
WoW!! 3 hours and not one reply,I can see it's gonna be a **BUMP** day :rolleyes:

---

### Post by KiwiNZ on 2006-12-01
patience is a virtue

---

### Post by doobit on 2006-12-01
Since these are internal modems, try lspci and post the outputs here. Then run dmesg and see if any drivers are loaded.
Also, since the develppers have offered to help with that particular program (that's in the the "read the FAQ" part) have you tried emailing them yet?
I'm interested in this as well, although I have broadband, because I would like to help a friend who only has dialup.

---

