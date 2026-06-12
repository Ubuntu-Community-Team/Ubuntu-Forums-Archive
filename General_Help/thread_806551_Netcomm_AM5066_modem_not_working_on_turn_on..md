---
title: "Netcomm AM5066 modem not working on turn on."
date: 2008-05-25
forum: General Help
---

### Post by Neil Dugan on 2008-05-25
Hi,

I have a Netcomm AM5066 RaveIII usb modem. using the driver from HSF driver from Conexant.

When I turn on the computer the modem does show up with lsusb, the driver is visible with lsmod, but the modem isn't working. :(  If I unplug the modem and then insert it every goes correctly. :)

When I reset the computer there isn't any trouble ether.  So I am presuming that something needs to be sent to the modem after power up, to get it to work.


$ dmesg | grep modem -
[20638.463428] /usr/lib/hsfmodem/modules/osusb.c: CD2_GET_INFROMATION returned error -71
[20638.463447] /usr/lib/hsfmodem/modules/cnxthwusb_common.c: Firmware download failed
[20638.467436] /usr/lib/hsfmodem/modules/cnxthwusb_common.c: CommInterface already claimed

$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0572:1300 Conexant Systems (Rockwell), Inc. 
Bus 001 Device 001: ID 0000:0000 

Is this a bug in the USB system ?
Is there some command I can run that simulates a device being unplugged and reinserted ?

---

