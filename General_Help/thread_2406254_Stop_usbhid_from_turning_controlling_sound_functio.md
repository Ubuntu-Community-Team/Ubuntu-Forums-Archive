---
title: "Stop usbhid from turning controlling sound functions based on GPIO input."
date: 2018-11-18
forum: General Help
---

### Post by samuelrock on 2018-11-18
I have a sound card from C-Media it is a CM108 the device has 4 GPIOs exposed on the board. I am a Ham Radio Operator and it is common place to modify the CM108 devices to work as a radio controller. For the most part this is done on a server with no GUI and a channel driver is loaded by asterisk that takes over the card. 

On my desktop Ubuntu Mate 18.04 I have installed a APRS program called Dire Wolf that also has the ability to use this CM108 device. When using it in Dire Wolf every time my radio receives a signal the volume on my sound card is turned down. This is because that GPIO is the Volume Down button. This is also the GPIO that they use for the input to tell the computer the radio is in receive mode. 

I would like to prevent the usbhid from controlling the sound but keep the GPIO accessible to the system so I can use the GPIOs on the USB Sound card to control a radio. I have several homemade and commercial devices that that use the C-Media family of chips that have this issue. The devices in the chip family are CM108, CM109, and CM119 also two knock off chips SSS1621 and SSS1623 that were sourced from china.

Output of usb-devices 
```


T:  Bus=01 Lev=02 Prnt=04 Port=03 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0d8c ProdID=013c Rev=01.00
S:  Manufacturer=C-Media Electronics Inc.      
S:  Product=USB PnP Sound Device
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid




```

Link to the C code that makes the CM108 work with DireWolf
[https://github.com/wb2osz/direwolf/blob/master/cm108.c](https://github.com/wb2osz/direwolf/blob/master/cm108.c)

Link to the C code that makes the CM108 work with Asterisk
[https://github.com/rillian/asterisk-opus/blob/master/channels/chan_usbradio.c](https://github.com/rillian/asterisk-opus/blob/master/channels/chan_usbradio.c)

Outline of the mods to the CM device
[http://www.repeater-builder.com/projects/fob/syba71-fob.html](http://www.repeater-builder.com/projects/fob/syba71-fob.html)


Let me know if you have any ideas how I can break the tie to my sound controller or if you need any other information..  I have been trying to figure something out on this for a few days now.


Thanks
Sam

---

