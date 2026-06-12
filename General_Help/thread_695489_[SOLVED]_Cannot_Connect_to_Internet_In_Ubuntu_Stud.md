---
title: "[SOLVED] Cannot Connect to Internet In Ubuntu Studio 7.10"
date: 2008-02-13
forum: General Help
---

### Post by stuartwood89 on 2008-02-13
I'm having a hard time connecting to the internet in 7.10.  My connection is set up like this:
Internet ->Wired router->My PC
My machine has a built in ethernet adaptor on the motherboard.  I was also asked to find the output of 'lspci' in an earlier thread:

```
stuartwood89@Ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6238
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
04:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
06:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
07:08.0 USB Controller: NEC Corporation USB (rev 43)
07:08.1 USB Controller: NEC Corporation USB (rev 43)
07:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

If I type 'lshw -C network' I get:

```
stuartwood89@Ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:18:f3:c0:bd:c3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 module=atl1 multicast=yes
```

Hope this enough information for you!

Help is very much appreciated.

---

### Post by zvacet on 2008-02-13
Upper right on panel>network manager>manual config>network>select your modem(don´t tick it just click on it)>properties>select your type of connection8dhcp or static)>close>DNS tab>you will see one address and it is probably from your router so leave it and add your nameservers>general>tick your modem ans you should see window with message** changing network interfaces**.When that is done programs<accessories>terminal

```
pppoeconf
```

---

### Post by stuartwood89 on 2008-02-13
The closest I could find is this:

[IMG]http://i147.photobucket.com/albums/r315/stuartwood1989/Screenshot.png[/IMG]

But even the icon in the top right I had to add.  The 'configure' button is disabled.  I've tried other things but I can't find any addresses.  Bear in mind I am completely new to this and I know nothing about networking down to this level.

---

### Post by zvacet on 2008-02-13
It should look like in attachment,but you can just select eth0 instead of lo from what I´m see on your screenshot.When you select** eth0** then go with **configure**.

---

### Post by stuartwood89 on 2008-02-13
Yeah I added 'eth0' to the list and pushed 'configure', and I managed to get a few more things sorted, including adding my IP address.  So now I type 'pppoeconf' and it scans for something, but I get this:

[IMG]http://i147.photobucket.com/albums/r315/stuartwood1989/Screenshot-1.png[/IMG]

At least I'm getting further than last time.

---

### Post by stuartwood89 on 2008-02-14
Would I need to find out the address of my router by any chance?  I need to get this working as soon as possible.

Help is greatly appreciated and *desperately needed*!

---

### Post by zvacet on 2008-02-14
Try with [this](https://help.ubuntu.com/community/Router).

---

### Post by stuartwood89 on 2008-02-14
What if, instead of using 'eth0', I use 'eth1'? (which according to this link, suggests that my network adaptor is connected to a switch or hub)

I'll try it when I get home and I'll post the outcome.

---

### Post by stuartwood89 on 2008-02-14
...So that didn't work 'couldn't find interface'.  So I'm out of ideas.  But tell me: If I went out and bought a seperate Network Interface Card, thereby replacing the one built into my motherboard, would I have problems then?

Any more suggestions?

---

### Post by zvacet on 2008-02-14
It can not find it because you change it from eth0 to eth1.If you don´t know your router address you can find it in Windows>conestions>LAN>properties.Same setting you will use in Ubuntu(obviously).That is all I can think of rght now.Sorry if it is not good enough.

---

### Post by stuartwood89 on 2008-02-14
Ok this is wierd.  I found my connection in Windows, and wrote down my IP, and some other bits of info,  I still tried to run 'pppoeconf' and I got the same message.  I tried opening Firefox just in case and it works!  I'm writing this now from Ubuntu!  Thanks for all your help!

EDIT:: I haven't restarted yet so I'm not 100% certain that settings will be saved for when I start back up again.

---

### Post by zvacet on 2008-02-15
I´m glad you are making progress.

---

### Post by stuartwood89 on 2008-02-15
Yep, seems to be working fine now, and that's after numerous restarts, so thanks again for your help!

---

