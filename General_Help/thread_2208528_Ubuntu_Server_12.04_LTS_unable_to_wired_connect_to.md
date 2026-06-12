---
title: "Ubuntu Server 12.04 LTS unable to wired connect to internet"
date: 2014-02-28
forum: General Help
---

### Post by Hanjaya on 2014-02-28
I installed Ubuntu Server 12.04LTS on my old Dell Inspiron laptop (Dual Core). I wired connected to my router but it is unable to connect.

Here are some info.

```

ubuntu:~$ ifconfig

l0      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING   MTU:65536   Metric:1
        RX packets:8  errors:0  dropped:0  overruns:0  frame:0
        TX packets:8  errors:0  dropped:0  overruns:0  carrier:0
        Collisions:0  txqueuelen:0
        RX bytes:552  (552.0 B)   TX bytes:552  (552.2 B)

``` 

/etc/network/interfaces
```

Auto l0
iface l0 inet loopback

```

My resolv.conf is blank.

Please help.

Thanks.

hc.

---

### Post by Iowan on 2014-02-28
It may not matter, but the loopback device is normally identified with "lo", not "l0".
Dunno if it'd help to change it.

I see no other devices listed. You might check (post):
```
sudo lshw -C network
```

---

### Post by Hanjaya on 2014-02-28
Hi,

Sorry "Lo" thing is my mistake, I re-wrote the message from screenshot instead of copy paste it. 

Yes, I supposed to see "eth0" on ifconfig. Anyway, I will later check 

sudo lshw -C network

---

### Post by cariboo on 2014-03-01
Moved to General Help.

---

### Post by Hanjaya on 2014-03-02
lshw -C network

```
*-network
          description: Network controller
          product: BCM4311 802.11b/g WLAN
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:0c:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=b43-pci-bridge latency=0
          resources: irq:17 memory:efdfc000-efdfffff
*-network DISABLED
         description: Ethernet interface
          product: BCM4401-B0 100Base-TX
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: eth0
          version: 02
          serial: 00:15:c5:7b:10:27
          capacity: 100Mbit/s
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list Ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
          resources: irq:17 memory:ef9fe000-ef9fffff
```

---

### Post by Hanjaya on 2014-03-02
I added this line to /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet dhcp 

The lshw -C network result shows the Ethernet interface is not disabled any longer but when I ping yahoo.com, it still shows unknown host.

Hc.

---

### Post by steeldriver on 2014-03-02
Is your /etc/resolv.conf still empty? does your DHCP server provide a list of DNS servers? if not, you may need to add a dns-nameservers line

---

### Post by Hanjaya on 2014-03-06
Hi,

The /etc/resolv.conf is not empty now, it has: nameserver 127.0.0.1

How do I do the dns nameserver?

Thanks.

Hc.

---

### Post by varunendra on 2014-03-06
> **Hanjaya said:**
> lshw -C network

```

*-network **[COLOR="#FF0000"]DISABLED[/COLOR]**
         description: Ethernet interface
          product: BCM4401-B0 100Base-TX
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: eth0
          version: 02
          serial: 00:15:c5:7b:10:27
          capacity: 100Mbit/s
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list Ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes **driver=[COLOR="#006400"]b44[/COLOR]** driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
          resources: irq:17 memory:ef9fe000-ef9fffff
```
The Ethernet interface is disabled, despite the fact that the required driver (b44) is natively available.

Have you, by any chance, installed the "wl" driver? It blacklists the b44 and ssb drivers that are required to activate your ethernet card.

Please check -
```
lsmod | egrep 'b44|ssb|wl'
```
Which ones do you see? Is "wl" there? If yes, please try -
```
sudo apt-get purge bcmwl-kernel-source
```
..followed by a reboot. Then check -
```
sudo lshw -C network
```
..again. Is the status "DISABLED" gone?

---

### Post by Hanjaya on 2014-03-06
Hi Varunendra,

I have added this line to [COLOR=#000000]/etc/network/interfaces 
[/COLOR]
```
[COLOR=#000000]# The primary network interface[/COLOR]
[COLOR=#000000]auto eth0[/COLOR]
[COLOR=#000000]iface eth0 inet dhcp [/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

When I [/COLOR]*[COLOR=#000000]lshw -C network [/COLOR]*[COLOR=#000000]the Ethernet Interface networks [/COLOR][COLOR=#000000]is no longer disabled.

Do you want me to remove the above lines that I added to /etc/network/interface before doing your steps?

Thanks.

hc.[/COLOR]

---

### Post by varunendra on 2014-03-06
> **Hanjaya said:**
> Do you want me to remove the above lines that I added to /etc/network/interface before doing your steps?

Assuming you don't have a GUI and don't use NetworkManager, you do need to keep those lines there.

But do you have a DHCP server on the network (usually the router performs this role)? Is it working properly?

What are the current outputs of -
```
ifconfig -a
route -n
cat /etc/resolv.conf
ping -c4 *<your gateway>*
```

---

### Post by Hanjaya on 2014-03-08
Hi,

Ifconfig -a

```

eth0          Link encap:Ethernet HWaddr 00:15:c5:7b:10:27
                  inet addr:10.0.0.6 Bcast:10.0.0.255 Mask:255.255.255.0
                  inet6 addr: fe80::215:c5ff:fe7b:1027/64  Scope:Link
                  UP BROADCAST RUNNING   MULTICAST MTU:1500   Metric:1
                  RX packets:8  errors:0  dropped:0  overruns:0  frame:0
                  TX packets:11 errors:0  dropped:0  overruns:0  carrier:0
                  Collisions:0  txqueuelen:1000
                 RX bytes:2632 (2.6 KB)   TX bytes:1940 (1.9 KB)
                 Interrupt: 17

lo.         Link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr:  ::1/128 Scope:Host
             UP LOOPBACK RUNNING   MTU:65536   Metric:1
             RX packets:40 errors:0  dropped:0  overruns:0  frame:0
        TX packets:40 errors:0  dropped:0  overruns:0  carrier:0
        Collisions:0  txqueuelen:0
        RX bytes:2976 (2.9 KB)   TX bytes:2976  (2.9 KB)
```

route -n
```

Kernel IP routing table
Destination.         Gateway.         Genmask.         Flags.  Metric.  Ref.    Use.  Iface
0.0.0.0.                 10.0.0.1.          0.0.0.0.               UG.      100.       0.        0.      eth0
10.0.0.0.               0.0.0.0.            255.255.255.0.  U.         0.           0.        0.      eth0

```

I only saw 'b44' and 'ssb', no 'wl'.

Thanks.

Hc.

---

