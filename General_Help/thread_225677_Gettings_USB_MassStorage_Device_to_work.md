---
title: "Gettings USB MassStorage Device to work"
date: 2006-07-30
forum: General Help
---

### Post by ticool on 2006-07-30
Hello everyone this is my second try, i searched the forum, i asked google, i got a lot of interesting stuff to know, but all this didn't helped me out of this misery.

At First i bought me a new mp3 player, Philips HDD6230 ( 30 GB ) should work as USB MassStorage device and as MTP Player device.

That't what lsusb says about that drive :
```

Bus 003 Device 002: ID 0471:014b Philips

```

My Problem is, that my box recognizes the drive, but didn't activate the scsi emulation to access this drive as USB MassStorge

There are a lot of hints for that Problem, like modprobe usb_storage or modprobe -r ehci_hcd to remove this USB Mode which seems to be help for VIA Chipsets but mine is a Nforce2 ;)

lsmod | grep usb gives the following output after loading the module usb_storage with modprobe:
```

usb_storage            80000  0
usbhid                 41312  0
usbcore               137476  5 usb_storage,usbhid,ehci_hcd,ohci_hcd
scsi_mod              145736  2 usb_storage,libata

```

dmesg only gives back that it recognizes the drive :

```

Jul 30 10:04:37 ticool-desktop kernel: [4295533.625000] usb 3-3: new high speed USB device using ehci_hcd and address 4

```

nothing more :(


My current Kernel is 2.6.15-23-k7 using Kubuntu Dapper
I did try the new kernel in the repositorys but it didn't work either.

I'm really messed up with this problem, i working the second day on it and  
now i'm stuck.

Hopefully anybody has a hint for me!


Thanks a lot

ticool

---

### Post by x64Jimbo on 2006-07-30
First thing I'd recommend is scanning to see what device slot it's occupying.
Uncomment your universe repos in /etc/apt/sources.list
sudo aptitude install sg3-utils
sg_scan -i
this will give you a list of your devices at a hardware level
next, do this:
sg_map
This will list the hardware devices' locations in the system. Their /dev locations. 

So, find your device location (probably /dev/sdxx) and then attempt to mount it like this:
mkdir /mnt/sdxx
sudo mount /dev/sdxx /mnt/sdxx

For more info, check out the tutorial that I gleaned this knowledge from earlier today:
[http://www.cs.sfu.ca/~ggbaker/personal/cf-linux](http://www.cs.sfu.ca/~ggbaker/personal/cf-linux)

---

### Post by ticool on 2006-07-30
Thanks for your answer, well this thing seems to be a bit wired.
sg3utils didn't find anything.
cat /proc/bus/usb/devices gives me the following output for my device:

```

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0471 ProdID=014b Rev= 0.01
S:  Manufacturer=Philips
S:  Product=Philips HDD63XX GoGear
S:  SerialNumber=           85110438M
C:* #Ifs= 1 Cfg#=128 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS= 512 Ivl=1ms

```

Driver=(none) 
Hm...

---

### Post by x64Jimbo on 2006-07-30
> **ticool said:**
> Thanks for your answer, well this thing seems to be a bit wired.
sg3utils didn't find anything.
cat /proc/bus/usb/devices gives me the following output for my device:

```

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0471 ProdID=014b Rev= 0.01
S:  Manufacturer=Philips
S:  Product=Philips HDD63XX GoGear
S:  SerialNumber=           85110438M
C:* #Ifs= 1 Cfg#=128 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS= 512 Ivl=1ms

```

Driver=(none) 
Hm...
Are you sure that it's a standard "generic mass storage" device? It might need a proprietary driver to work, which could severely hinder you. If all else fails, get VMWare and get a virtual Windows 98* running inside it with USB passthrough to get the device talking straight to that virtual machine.

*I only suggest Win98 because it's pretty fast in a virtual environment and if you're only going to use it for one task, it should do the trick nicely.

---

