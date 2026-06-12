---
title: "well i may have found my internet problem"
date: 2022-11-15
forum: General Help
---

### Post by cryofreeze666 on 2022-11-15
x570 unify motherboard, uses a realtek rtl l8125 2.5 g lan controller.  contacted msi directly, they came to the conclusion that i may need to reinstall the drivers for my ethernet controller, only thing i can figure is that the open source version of the ethernet driver that should have loaded with the installation didn't because my networking problem.  every time i turn on the computer to begin working with it, i need to turn the network off then back on to connect to internet.  so if someone could tell me the name of the open source driver so i can type it into the orange bag ap i'd appreciate it.  maybe that will fix things for me.  again the ethernet controller is a realtek rtl l8125 2.5 g lan controller (wired).  thank you in advance.

---

### Post by grahammechanical on 2022-11-15
We do not install wireless or ethernet drivers through Ubuntu Software.

Please run this command and post the output in quote tags.

```
lshw -C network
```

Here is what I get.

> -network
       description: Ethernet interface
       product: Ethernet Connection (10) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: 80:fa:5b:9d:b0:5c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.15.0-52-generic firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:128 memory:b1400000-b141ffff

Notice this information:

> broadcast=yes driver=e1000e driverversion=5.15.0-52-generic

That tells me that the ethernet adapter is working and that there is an ethernet driver and it is installed. What does that command tell you about your ethernet adapter.

Regards

---

### Post by HermanAB on 2022-11-16
There is a utility called ethtool, which may be useful.

---

### Post by cryofreeze666 on 2022-12-03
it is telling me this:
 WARNING: you should run this program as super-user.
   *-network                  
        description: Ethernet interface
        product: RTL8125 2.5GbE Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:27:00.0
        logical name: enp39s0
        version: 00
        serial: d8:bb:c1:a6:7c:1b
        capacity: 1Gbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-53-generic duplex=full firmware=rtl8125a-3_0.0.1 08/24/19 ip=192.168.0.76 latency=0 link=yes multicast=yes port=twisted pair
        resources: irq:37 ioport:f000(size=256) memory:fc600000-fc60ffff memory:fc610000-fc613fff memory:fc620000-fc68ffff memory:fc690000-fc6abfff
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
 a@a-MS-7C35:~/Desktop$ 

IT SEEMS TO BE INSTALLED QUITE WELL.  think i'm going to take one of the 2.5g ethernet cards of the shelf connect it and see what happens.  i am not expecting a change but that will also get me closer to the root of the problem i think. especially if i managed to get bad hardware.

---

### Post by HermanAB on 2022-12-03
Statistics:
$ sudo ethtool -S

---

### Post by cryofreeze666 on 2022-12-10
dont know what that command line is supposed to do but, this is what happened after typing it in.

a@a-MS-7C35:~/Desktop$ sudo ethtool -S
[sudo] password for a: 
sudo: ethtool: command not found
a@a-MS-7C35:~/Desktop$

---

### Post by HermanAB on 2022-12-10
You should install ethtool if you want to do ethernet fault finding

---

### Post by TheFu on 2022-12-10
My quick google-fu says the correct driver is r8125, so I'd verify that is on the system already (I'd use 'locate' ) and if it is since it has been part of the kernel since v5.4.x, then I'd blacklist the module that the kernel has decided should be used.  If it isn't, perhaps a bug report can get Canonical to include it?

[https://forums.linuxmint.com/viewtopic.php?f=52&t=361709](https://forums.linuxmint.com/viewtopic.php?f=52&t=361709) has a Linux Mint how-to for this driver.  The exact version will/should be different, but there's a link to get the driver.  If this is still needed 2+ yrs after the card and drivers were released, well, ... cough.  Is there hatred between Linux,  Canonical and Realtek that prevents a cleaner interface when new drivers are available?

Realtek drivers and NICs have a real problem finding the correct driver to be used. This has been happening long enough that I simply avoid any NIC or motherboard that comes with realtek networking.  Life is much easier and networking "just works™" when there isn't any realtek.  The $20 extra cost to get anything other than realtek is worth it to me. YMMV.

---

