---
title: "connection script failed, verison usb720"
date: 2007-09-14
forum: General Help
---

### Post by sarahsilverman on 2007-09-14
hello, i have no internet connection except for this usb thingy. i used this script thingy:

/etc/modprobe.d/options:
# Options for u720
options usbserial vendor=0×1410 product=0×2110
options airprime endpoints=1

/etc/modules:
usbserial
airprime

/etc/ppp/peers/verizon:
noauth
connect “/usr/sbin/chat -v -f /etc/ppp/peers/verizon_chat”
defaultroute
usepeerdns
ttyUSB0
230400
local
debug
-detach

/etc/ppp/peers/verizon_chat:
‘’ ‘ATZ’
‘OK’ ‘ATDT#777?
‘CONNECT’ ‘’

# sudo pppd call verizon

but it says connection script failed

what am i doing wrong, how can i install it?

i am a total newbie at this linux stuff, please try explain this in newbie language.

any help is greatly appreciated thanks :popcorn:

---

### Post by sarahsilverman on 2007-09-14
ps: im using my sisters internet on her mac, i don't have much time here. please do help.

---

