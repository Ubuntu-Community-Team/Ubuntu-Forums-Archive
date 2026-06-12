---
title: "Dial-up connection in Gutsy  / linux (Modem drivers already working)"
date: 2007-12-22
forum: General Help
---

### Post by weblordpepe on 2007-12-22
Hello there guys. I have a working dial-up modem & driver, however I cannot establish a connection to my ISP.

I have tried many different methods, but the guts of the problem is establishing PPP and TCP/IP.
My modem lives on **/dev/ttySL0**

After my IPS responds & prompts for username & password, it then prompts to enter a choice of either **network**, **login** or **PPP**

This is what **Gnome PPP** says when I try & connect:
It doesn't seem to 'click' when the PPP session starts. Here have a look:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53972&stc=1&d=1198323246[/IMG]

The modem toolbar applet doesn't let me connect up either, it just says 'Could not get connection time'.

Using **wvdialconf** produces the following output:
> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



The contents of my **/etc/wvdial.conf** are as follows:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = **not telling**
Idle Seconds = 180
Modem Type = Analog Modem
Stupid Mode = false
Baud = 460800
New PPPD = true
Modem = /dev/ttySL0
ISDN = 0
Username = bill-gates
; Phone = <Target Phone Number>
Product = xtra

[Dialer xtra]
Username = bill-gates
Password = **not telling**
Phone = 087303030



Running **wvdial xtra** produces the following:> 
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<Notice>: Idle Seconds = 180, disabling automatic reconnect.
WvDial<*1>: Sending: ATDT087303030
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT087303030
WvDial Modem<*1>: CONNECT 53333
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial<Err>: Connected, but carrier signal lost!  Retrying...
WvDial<*1>: Sending: ATDT087303030
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>:  
WvDial Modem<*1>: login: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT087303030
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT087303030






Can someone give me a hand with this? I have tried using pppd, and pppconfig but nothing seems to work.

---

### Post by weblordpepe on 2007-12-23
Ok I found out that by using **pppconfig** I can specify 'post login chat' which deals with ISP prompting for stuff after one has logged in successfully.
I can now use **pon xtra** to connect to the ISP. Although there is still no way to do this in the GUI.
Although that connected the PPP session, nothing else would work.

I had to specify the routing table manually. I then had to add a DNS server manually. There was an option to put after **pon** to say **defaultroute** although I don't know if it did anything.

---

