---
title: "USB MIDI device not loading"
date: 2007-08-08
forum: General Help
---

### Post by BobvanderPoel on 2007-08-08
I am quite sure that this _used_ to work. But, something did something bad :)

I have a USB M-Audio Midi Interface. It is plugged into one of the midi ports on the computer. For some reason it is not being "found" when the computer boots. I say "found" because when I do a  "cat /proc/bus/usb/devices" it does show up:

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0763 ProdID=0150 Rev= 1.25
S:  Manufacturer=M-Audio
S:  Product=USB Uno MIDI Interface
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=01(audio) Sub=03 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

But, the command lsusb does NOT list it:

bob$ lsusb
Bus 002 Device 005: ID 0ea0:2126 Ours Technology, Inc. 7-in-1 Card Reader
Bus 002 Device 004: ID 1058:0901 Western Digital Technologies, Inc.
Bus 002 Device 003: ID 03f0:1c17 Hewlett-Packard Color LaserJet 2550l
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Nor does my midiplayer, aplaymidi, find it:

bob$ aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    M Audio Audiophile 24/96         M Audio Audiophile 24/96 MIDI
 20:0    MPU-401 UART                     MPU-401 UART MIDI

However, if I unplug/plug the device all is well. Other than not rebooting my computer ... any suggestions?

I did find a shell script "reset-scsi-bus.sh", but no luck with that.

Thanks.

---

### Post by BobvanderPoel on 2007-08-08
Very odd, all this :) I just noticed that the power to my Epson USB scanner had been unplugged, but the scanner was still connected to the usb. I connected the power and rebooted. This time the USB-UNO was found. Is this just a lucky hit, or could it be that the having an unpowered device on one port is screwing up a 2nd device? Oh, appears that both the scanner and UNO are on ths same bus:

lsusb
Bus 002 Device 006: ID 0ea0:2126 Ours Technology, Inc. 7-in-1 Card Reader
Bus 002 Device 005: ID 1058:0901 Western Digital Technologies, Inc.
Bus 002 Device 004: ID 03f0:1c17 Hewlett-Packard Color LaserJet 2550l
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0763:0150 Midiman
Bus 001 Device 003: ID 04b8:011d Seiko Epson Corp. Perfection 1260 Photo
Bus 001 Device 001: ID 0000:0000

There has to be some magic going on with all this.

---

### Post by DagMan on 2007-08-08
If you're trying to mount it on boot, then perhaps sticking it in fstab without the commonly used noauto option?

---

### Post by BobvanderPoel on 2007-08-08
Ummm ... fstab? No this is not a media device. It's a MIDI interface. I don't think you can put things like that in an fstab since there is no filesystem. I stand to be corrected.

But, as I said in my reply to myself, now that the scanner has power it all seems to work. Still think it's odd, though.

---

### Post by fredj on 2007-08-09
Its not that strange if the two USB ports are on the same hub. Each hub can supply at most 
500ma at 5v and it is possible that your midi device needs all or almost all of this to work.
The unpowered scanner may itself draw some power from the hub causing the supply to drop 
below what the midi device needs or it may upset data transmission through the hub.

---

### Post by BobvanderPoel on 2007-08-10
> **fredj said:**
> Its not that strange if the two USB ports are on the same hub. Each hub can supply at most 
500ma at 5v and it is possible that your midi device needs all or almost all of this to work.
The unpowered scanner may itself draw some power from the hub causing the supply to drop 
below what the midi device needs or it may upset data transmission through the hub.

Yes, in this case the 2 devices are on the same port/port.

Bus 001 Device 004: ID 0763:0150 Midiman
Bus 001 Device 003: ID 04b8:011d Seiko Epson Corp. Perfection 1260 Photo

I'm sure you are correct on this. But, how would replugging the Midi device, while still having the sanner plugged but unpowered permit the system to load the midi? I assume the the tolerances are very close and it's all a matter of luck :)

---

