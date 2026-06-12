---
title: "Trouble detecting ethernet port"
date: 2008-06-10
forum: General Help
---

### Post by Arenlor on 2008-06-10
I have a laptop I'm trying to set up a server on and for some reason it doesn't see the ethernet port on itself, only the wireless. It's a Toshiba Satellite. I would like to be able to use ethernet with it as it's going to be a local server (LAMP and Samba) and my router uses WPA Personal and I'm not sure how to enable WPA with it. I don't plan on rebooting it at all truly so having it attached to ethernet would be best, though instructions on how to set up WPA on it would be good too.

---

### Post by ben@layer on 2008-06-10
I am new(1year)to but mabe I can help
type lspci in the console
in copy it to the forums

---

### Post by Arenlor on 2008-06-10
arenlor@thommy:~/www$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

---

### Post by ben@layer on 2008-06-11
I need more info what Ubuntu version you using if 7.10 or lower download a live CD of 8.04 or mandriva for thy have more drivers. than do lspci and see if Ethernet controller shows up on them 
mine show up like these but yours mite be deferent

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I don't Know how mach more I can help

ps: sorry for my spelling

---

### Post by Arenlor on 2008-06-11
I'm running Hardy Heron, I'll try a live CD later today.

---

### Post by Arenlor on 2008-06-17
I installed toshset but no luck. When I try to use it to see if it'll enable it, I get the following (alias toshset="sudo toshset")
```
arenlor@thommy:~$ toshset -lan enable
SciFeature:action: error setting LAN controller
        SciSet returned: unknown error. (244)
```

---

### Post by iaculallad on 2008-06-17
Try to post the output of:

```
dmesg |grep eth0
```

---

### Post by Arenlor on 2008-06-17
```
arenlor@thommy:~$ dmesg | grep eth0
[  276.487446] eth0: Hardware identity 0005:0004:0005:0000
[  276.487564] eth0: Station identity  001f:0001:0008:000a
[  276.487568] eth0: Firmware determined as Lucent/Agere 8.10
[  276.487571] eth0: Ad-hoc demo mode supported
[  276.487573] eth0: IEEE standard IBSS ad-hoc mode supported
[  276.487575] eth0: WEP supported, 104-bit key
[  276.487654] eth0: MAC address 00:02:2d:b0:e7:10
[  276.487749] eth0: Station name "HERMES I"
[  276.488308] eth0: ready
[  276.488682] eth0: orinoco_cs at 0.0, irq 11, io 0x0100-0x013f
[  276.652943] eth0: New link status: Disconnected (0002)
[  276.762843] eth0: New link status: Connected (0001)
[  308.830819] eth0: no IPv6 routers present
[  462.594431] eth0: New link status: AP Out of Range (0004)
[  463.145074] eth0: New link status: AP In Range (0005)
[  463.350855] eth0: New link status: Disconnected (0002)
[  463.481746] eth0: New link status: Connected (0001)
```
Also:
```
arenlor@thommy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2d:b0:e7:10
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:feb0:e710/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2018 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:682406 (666.4 KB)  TX bytes:470466 (459.4 KB)
          Interrupt:11 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3600 (3.5 KB)  TX bytes:3600 (3.5 KB)
```
and:
```
arenlor@thommy:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"Arenlor"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:91:B6:B0
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/92  Signal level=-2 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:166
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0
```

---

