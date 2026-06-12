---
title: "HTC USB Modem + tty"
date: 2006-11-09
forum: General Help
---

### Post by FitzChivalry on 2006-11-09
Heya... I'm working on using my HTC TyTn/Hermes (T-Mobile MDA Vario) as a USB Modem.... I have the following configs setup:

**/etc/ppp/peers/gprs**
```
/dev/ttyUSB0
115200

crtscts
idle 300
lcp-echo-failure 0
lcp-echo-interval 0
local
lock
noauth
#nodetach
noipdefault
noipdefault
noproxyarp
defaultroute
usepeerdns
ipparam tmobile
user ''
connect "/usr/sbin/chat -f /etc/chatscripts/gprs"
```

**/etc/ppp/chatscripts/gprs**
```
SAY 'Starting GPRS connect script. please work\n'
TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
"" ATZ
SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"IP","general.t-mobile.uk"'
SAY 'Dialing...\n'
OK ATD*99#
CONNECT ' '
```

I get this error when running 'pppd call gprs':
```
pppd: In file /etc/ppp/peers/gprs: Unrecognized option '/dev/ttyUSB0'
```

What would I need to change this too? sda* doesn't show up when I connect the phone in (it's Windows Mobile 5 based, but I'm running the Wireless Modem function in it)

Thanks

---

### Post by wintersommer on 2006-12-02
/dev/ttyUSB0 does not exist, thats why you get this message.
If its existing it goes away.

load usbserial vendor= product= and you will see in your kernel log something with ttyUSB0... :>

---

