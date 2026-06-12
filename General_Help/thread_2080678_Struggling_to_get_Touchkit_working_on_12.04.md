---
title: "Struggling to get Touchkit working on 12.04"
date: 2012-11-04
forum: General Help
---

### Post by Diddley on 2012-11-04
I have recently installed 12.04LTS on an Intel Atom desktop (dual boot w/ Win7).
Everything is running well, but unfortunately I can't get my touchscreen working.

The monitor is a BenQ AD702 Touch screen and works perfectly with Win7 and OS X, so I know its not a hardware problem. The Touch screen interface is USB.

lsusb yields the following:
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano  Transceiver v1.0 for Bluetooth
 Bus 004 Device 003: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

xinput =>

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0	id=9	[slave  keyboard (3)]

I've tried finding and downloading drivers, but all available on the website are for significantly older versions of Linux.

Any suggestions?

---

