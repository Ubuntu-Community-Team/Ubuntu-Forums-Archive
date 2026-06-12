---
title: "Internet not working"
date: 2007-05-03
forum: General Help
---

### Post by dunedust on 2007-05-03
My net connection doesn't seem to be working 
I connect through a lan card 
It connects just fine but none of the programs (firefox , kopete,azureus) work
Im pasting a few command outputs below.

```

prometheus@prometheus-desktop:~$ dmesg | grep eth
[17179586.764000] eth0: RealTek RTL8139 at 0xdc860000, 00:16:76:6c:7b:d9, IRQ 169
[17179586.764000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179587.000000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179601.060000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17180157.856000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180540.476000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```


```

prometheus@prometheus-desktop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a33 (rev 01)
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 30100000-301fffff
        Prefetchable memory behind bridge: 20000000-2fffffff
        Capabilities: <access denied>

00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 177
        I/O ports at 3068 [size=8]
        I/O ports at 3084 [size=4]
        I/O ports at 3060 [size=8]
        I/O ports at 3080 [size=4]
        I/O ports at 3030 [size=16]
        Memory at 30207600 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 30280000 [disabled] [size=512K]
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 185
        I/O ports at 3058 [size=8]
        I/O ports at 307c [size=4]
        I/O ports at 3050 [size=8]
        I/O ports at 3078 [size=4]
        I/O ports at 3020 [size=16]
        Memory at 30207400 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 30300000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at 30204000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at 30205000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at 30206000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Intel Corporation Unknown device d601
        Flags: 66MHz, medium devsel
        I/O ports at 3010 [size=16]
        Memory at 30207000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 3000 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, slow devsel, latency 64, IRQ 193
        Memory at 30200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 30000000-300fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA])
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 209
        Memory at 20000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at 30100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at 28000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Intel Corporation Unknown device d601
        Flags: bus master, medium devsel, latency 64, IRQ 169
        I/O ports at 1000 [size=256]
        Memory at 30000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```


```

prometheus@prometheus-desktop:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


```

```

prometheus@prometheus-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.082 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.035 ms

```

thanks for your help.

---

### Post by neouser99 on 2007-05-04
so post the output of these
```
ifconfig -a
```
```
route
```

-neo

---

### Post by dunedust on 2007-05-04
here
 ```

prometheus@prometheus-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:76:6C:7B:D9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21174 (20.6 KiB)  TX bytes:7357 (7.1 KiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:221.128.138.251  P-t-P:202.63.173.242  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:539 (539.0 b)  TX bytes:1963 (1.9 KiB)

```



```

prometheus@prometheus-desktop:~$ route
Kernel IP routing table
Destination       Gateway         Genmask             Flags Metric  Ref Use  Iface

202.63.173.242  *               255.255.255.255   UH     0         0        0    ppp0
default                 *               0.0.0.0                    U      0         0        0    ppp0

```

---

### Post by neouser99 on 2007-05-04
it looks like your routes are getting setup properly. i am unsure how to make that work with dsl though, so i don't know if someone else can help you, or if you can search around a little more on the forums for getting dsl setup within ubuntu.

-neo

---

### Post by dunedust on 2007-05-04
Can anyone please help 
ive been trying to get it to work since morning
i really cant use ubuntu without a net connection

ps: im having the same problem using the live cd

---

### Post by zvacet on 2007-05-04
You have just one card,do you?In your etc/network/interfsces it´s seems that you have more then one,and that one of them is wireless.If you have just eth0 let your etc/network/interfaces look like this
> prometheus@prometheus-desktop:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf




Go to the DNS tab and put your nameservers there.

```
pppoeconf
```

---

### Post by dunedust on 2007-05-04
Well i tried that 
but im still not able to connect
i have been using the same configuration for sic months or so and never had any problems

---

### Post by dunedust on 2007-05-05
<bump>

---

### Post by zvacet on 2007-05-05
O.K. If your connectionse to work just try to type in terminal

```
pon dsl-provider
```

That should trigger connection.

---

### Post by dunedust on 2007-05-05
My connection is triggered at boot up in most cases
when it doesn't i use pon dsl-provider

sudo pon dsl-provider gives the following output
 rp-pppoe.so loaded.

But whether i manually trigger it or it loads at boot up i still cant access the net

---

### Post by dunedust on 2007-05-05
This may sound weird but i just disconnected the data cable and plugged it back in 
and everything started working again 
I have restarted 2 -3 times and its all working fine 
thanks to everyone who helped me out   


ps: does anyone know why this might have happened?

---

### Post by mahiyar on 2007-05-05
You can thank me/us for that, our friendly worldnet isp has finally looked into the matter and resolved things.

---

### Post by mahiyar on 2007-05-05
What I would like to know from him (one Mr.Uttam) is that what exact changes in his configuration he did to resolve the problem so quickly, he was talking about some setting he had changed to enable some client to share documents.

---

