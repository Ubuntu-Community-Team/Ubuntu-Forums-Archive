---
title: "Trying to get my SD Card Reader to Work"
date: 2007-06-30
forum: General Help
---

### Post by climbjm on 2007-06-30
I have an SD card reader that is built into my laptop.
When I put my SD card into the laptop, it does not recognize it.
When I put my SD card into the laptop when booted into Windows, it works just fine.

**Are there any updates or packages anyone can think of that I should install?**

I tried searching for "SD" and I get thousands of results.
I tried searching for "SD Card" and "SD Memory" but haven't found what I am looking for.

Any help would be great, thanks in advance. :p

---

### Post by jasmuz on 2007-06-30
Could you open a terminal, and type : tail -f /var/log/messages
Then connect the card reader, please post the output.

---

### Post by climbjm on 2007-06-30
I sure hope this is what you were looking for.

```
Jun 30 21:51:04 jubuntu gconfd (root-17010): Exiting
Jun 30 21:52:37 jubuntu gconfd (root-17508): starting (version 2.18.0.1), pid 17508 user 'root'
Jun 30 21:52:37 jubuntu gconfd (root-17508): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 30 21:52:37 jubuntu gconfd (root-17508): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 30 21:52:37 jubuntu gconfd (root-17508): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 30 21:52:37 jubuntu gconfd (root-17508): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 30 21:52:37 jubuntu gconfd (root-17508): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 30 21:52:37 jubuntu kernel: [ 1737.012000] NTFS volume version 3.1.
Jun 30 21:53:07 jubuntu gconfd (root-17508): GConf server is not in use, shutting down.
Jun 30 21:53:07 jubuntu gconfd (root-17508): Exiting
```

---

### Post by dabl on 2007-07-01
What do you get from ```
lspci
``` in the console?  How about ```
lsusb
``` ?

In Edgy, I had to build a gspca driver to get my SD card reader to work, using this guidance: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).  But, in Feisty it "just works".

---

### Post by climbjm on 2007-07-01
**lspci**

```
0:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```

**lsusb**

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

