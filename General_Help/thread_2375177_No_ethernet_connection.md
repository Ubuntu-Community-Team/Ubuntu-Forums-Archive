---
title: "No ethernet connection"
date: 2017-10-22
forum: General Help
---

### Post by sam992 on 2017-10-22
[COLOR=#333333][FONT=Ubuntu]Cannot connect ethernet to internet.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Information:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]ifconfig[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lo Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:65536 Metric:1
     RX packets: 177 errors:0 dropped:0 overuns:0 frame:0
     TX packers: 177 errors:0 dropped:0 overuns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:12753 (12.7 KB) TX bytes:12753 (12.7 KB)[/FONT][/COLOR]

---

### Post by TheFu on 2017-10-22
a) please use "code tags" whenever posting commands AND output.  Makes things easier to read.  That's "Adv Reply" and the "#" button.

b) Appears that the correct driver for your NIC isn't loaded or the NIC is dead.  Please run **sudo lshw -C network** and post those results, so we can see which driver, if any is being used **and** what chips the NIC uses.

---

### Post by sam992 on 2017-10-22
> **TheFu said:**
> a) please use "code tags" whenever posting commands AND output.  Makes things easier to read.  That's "Adv Reply" and the "#" button.

b) Appears that the correct driver for your NIC isn't loaded or the NIC is dead.  Please run **sudo lshw -C network** and post those results, so we can see which driver, if any is being used **and** what chips the NIC uses.

PCI (sysfs)

---

### Post by Kris_M on 2017-10-22
credit beameup: This link:
```
https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04/622493#622493
```


Which says:
> I solved this error by deleting /etc/resolv.conf and recreating the symbolic link.


You can do that using the following commands:


```
sudo rm /etc/resolv.conf
sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
sudo resolvconf -u
```



execute those lines one at a time
I added 
```
sudo service network-manager restart
```

---

### Post by TheFu on 2017-10-22
> **sam992 said:**
> PCI (sysfs)

If that is the only output, then I would guess the NIC is dead.

Here's mine:
```
$ sudo lshw -C network -sanitize
  *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: bb
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-37-generic firmware=17.459231.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:47 memory:e1000000-e1001fff
  *-network:1
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.1
       logical name: enx000ec6c76418
       serial: [REMOVED]
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=[REMOVED] link=yes multicast=yes port=MII speed=1Gbit/s

```

---

