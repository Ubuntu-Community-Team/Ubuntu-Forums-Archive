---
title: "[SOLVED] Gigabyte U8000 digital TV Tuner"
date: 2008-07-09
forum: General Help
---

### Post by aresthedog on 2008-07-09
I need help setting Gigabyte GT-U8000-RH. 
link: [http://www.giga-byte.co.uk/Products/TVCard/Products_Overview.aspx?ClassValue=TV+Card&ProductID=2441&ProductName=GT-U8000-RH](http://www.giga-byte.co.uk/Products/TVCard/Products_Overview.aspx?ClassValue=TV+Card&ProductID=2441&ProductName=GT-U8000-RH)

lsusb: ID 1044:7002 Chu Yuen Enterprise Co., Ltd

TIA

---

### Post by Erlander on 2008-07-09
I suspect that this tuner is so new that linux developers have yet to write drivers for it.

Have a look at the linuxtv.org web site at:

[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

If you follow the links you can see all the supported hardware at present.

Rob

---

### Post by aresthedog on 2008-07-09
I think it is presented in Jun. 2007. I found some info:

[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB0700_USB2.0_DVB-T_devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB0700_USB2.0_DVB-T_devices)

---

### Post by Erlander on 2008-07-09
It looks as though you are in luck.

I would install Kaffeine and Me Tv from the repositories.

Hopefully one of them will work.

Also by entering dmesg in a terminal window you should be able to see among all the messages some referring to the tuner.  If you are still having trouble then post the output of dmesg here.

Rob

---

### Post by Erlander on 2008-07-10
The required driver is loaded by current kernels and can be found in /lib/firmware/2.6.24-19-generic.

The tuner should therefore work and as I said in my previous post I would try either or both of Kaffeine or Me Tv.

Rob

---

### Post by aresthedog on 2008-07-10
I can see drivers in /lib/firmware/2.6.24-19-generic. Looks like it depends on something else. MeTV or kaffeine cant find any video device.

When i plug in stick i get :
dmesg:
```
[  313.392037] usb 5-3: new high speed USB device using ehci_hcd and address 4
[  313.524847] usb 5-3: configuration #1 chosen from 1 choice
```

lsusb:
```
Bus 005 Device 004: ID 1044:7002 Chu Yuen Enterprise Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c046 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by Erlander on 2008-07-10
Yes, the firmware doesn't seem to be loading.  Perhaps if you copy the firmware file from where it is to one level higher ie /lib/firmware.
That is where I had to put mine when it wasn't in the kernel and had to be installed manually.  Since it is owned by root you will have to use sudo to copy it or if you want a graphical interface "gksudo nautilus"

I'm relatively new to all of this and am sorry I can't help more.

Here is the relevant part of my dmesg.

```
[  833.782580] usb 1-10: new high speed USB device using ehci_hcd and address 6
[  833.831965] usb 1-10: configuration #1 chosen from 1 choice
[  833.909643] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in cold state, will try to load a firmware
[  833.926815] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[  833.950518] usbcore: registered new interface driver dvb_usb_cxusb
[  833.962535] usb 1-10: USB disconnect, address 6
[  833.963472] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[  834.623217] usb 1-10: new high speed USB device using ehci_hcd and address 7
[  834.672136] usb 1-10: configuration #1 chosen from 1 choice
[  834.672286] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in warm state.
[  834.672506] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  834.676646] DVB: registering new adapter (DViCO FusionHDTV DVB-T USB (TH7579))
[  834.703247] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[  834.740688] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-10/input/input7
[  834.759407] dvb-usb: schedule remote query interval to 100 msecs.
[  834.759412] dvb-usb: DViCO FusionHDTV DVB-T USB (TH7579) successfully initialized and connected.
```

---

### Post by aresthedog on 2008-09-10
[http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html](http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html)

Works great !

---

### Post by saperduper on 2008-10-20
I followed the instructions given in this excellent howto **[http://www.linuxtv.org/wiki/index.php/Gigabyte_U8000-RH](http://www.linuxtv.org/wiki/index.php/Gigabyte_U8000-RH)** and it worked like a charm.

The sad thing is that currently **only DVB-T digital TV/HDTV is working** because there is **[COLOR="Red"]no driver written[/COLOR] for the CX25843-24Z audio/video decoder** which is probably used for the **analogue TV/FM radio** portion of the device.

---

