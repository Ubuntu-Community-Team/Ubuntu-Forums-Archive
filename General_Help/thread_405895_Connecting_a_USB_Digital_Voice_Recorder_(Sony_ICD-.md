---
title: "Connecting a USB Digital Voice Recorder (Sony ICD-P28 Voice Recorder)"
date: 2007-04-10
forum: General Help
---

### Post by Jvaldezjr on 2007-04-10
First off, I'm using Kubuntu Dapper.

I have 2 questions but this surrounds the problem I have of connecting and using a USB digital voice recorder.  The recorder I'm using is the Sony ICD-P28 model.  I know linux knows it's connected, and recognized, however I have no way of what device it is under /dev, nor do I know what driver to use (if one is being used at all).  Here is how I know linux knows what is connected (output from commands regarding the Sony device):

cat /proc/bus/usb/devices:
```
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=054c ProdID=0116 Rev= 1.00
S:  Manufacturer=Sony
S:  Product=Sony IC Recorder (P)
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

lsusb:
```
Bus 002 Device 004: ID 054c:0116 Sony Corp.
```

usbview (This is also listed under USB Devices in the KInfoCenter):
```
Sony IC Recorder (P)
Manufacturer: Sony
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: ff(vend.)
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 054c
Product Id: 0116
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 1
	Attributes: c0
	MaxPower Needed: 100mA

	Interface Number: 0
		Name: (none)
		Alternate Number: 0
		Class: ff(vend.) 
		Sub Class: 0
		Protocol: 0
		Number of Endpoints: 2

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms
```

Now linux knows its there and connected so maybe my problem is knowing what driver/module to use?  When I was using windows this was listed as a mass storage device, but I needed the Sony drivers to be able to use it.  So my questions are:
1 - Is there a way to create/convert the Sony windows driver into something usable in linux to be able to mount/use my device?
2 - Is there a generic module that will do the same thing as in #1?
3 - Am I screwed in regard to this device and will need to use VMWare to run windows to access the data on the recorder?

Thanks for taking the time to help.  I know some people had similiar problems with other brands of voice recorders (olympia, etc) and I searched documentation on them also, but no solution has been found so far.

---

### Post by MoonBlossom on 2008-01-10
Did you find a solution to this problem? I also have a Sony ICD-P28 and I can't use it on linux :(

---

### Post by Jvaldezjr on 2008-01-12
No I did not unfortunatley...however, because of my needs for a solid digital recorder, I bought an Olympus WS-300M digital recorder, and it is 10x better than the sony one I had.  This one plugs into linux and it is recognized as a USB storage device, so I can just copy over my voice files.  They also record in a wma format, which I'm not big about, however there are tools available to convert them to whatever format i choose (mp3, etc).  Look it up- it was well worth the purchase for me and the soudn quality is a million times better than my old Sony one.

---

### Post by MoonBlossom on 2008-01-12
Thank you so much for replying!

I guess I'll have to put for sale my old Sony recorder and get an Olympus. I don't really like having to use windows just to download what I recorded.

---

