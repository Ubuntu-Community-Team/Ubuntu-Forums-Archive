---
title: "wireless connection in Ubuntu 8.04"
date: 2008-05-10
forum: General Help
---

### Post by cosine352 on 2008-05-10
Hi friends,
I have just upgraded to Ubuntu 8.04 from Ubuntu 7.10. At first my wireless card was not working. Now I have managed to make it working by following this [instruction]("http://ubuntuforums.org/showthread.php?t=475963") (thanks for this good how to :guitar:)

Now my problem is the wireless card can not detect any signal (I use to get the signal with the same card in Ubuntu 7.10). Probably the hardware is not well integrated with the wireless software (??):confused: (windows xp can not get the signal (in the same computer). But Ubuntu 7.10 used to get. So I was very proud of Ubuntu.:)). 

Please help. 

Thanks

---

### Post by ghost_ryder35 on 2008-05-10
post the output of
```

sudo lspci

```

---

### Post by ghost_ryder35 on 2008-05-10
seeing the link you posted I am assuming you installed and configured the card with NDISwrapper?

---

### Post by cosine352 on 2008-05-10
Thanks for the quick reply ghost_ryder35,

> post the output of
Code:

sudo lspci



Here is the output

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: Trident Microsystems XGI Volari XP5 (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller


---

### Post by ghost_ryder35 on 2008-05-10
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
that is your network card. you can follow the link in my sig for the b43 how to as b43 driver replaced the bcm43xx driver. also you will need to remove ndiswrapper and blacklist ndiswrapper and bcm43xx 
```

sudo gedit /etc/modprobe.d/blacklist

```
put these lines in there
```

blacklist bcm43xx
blacklist ndiswrapper

```

---

### Post by cosine352 on 2008-05-10
> seeing the link you posted I am assuming you installed and configured the card with NDISwrapper?

I think so. Here is the output of lshw -C network
code
> lshw -C network

Output
> lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 02
       serial: 00:11:43:63:1a:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=10.244.16.134 latency=32 module=b44 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:96:f0:d4:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


---

### Post by cosine352 on 2008-05-10
> 02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
that is your network card. you can follow the link in my sig for the b43 how to as b43 driver replaced the bcm43xx driver. also you will need to remove ndiswrapper and blacklist ndiswrapper and bcm43xx

How do I remove ndiswrapeer and blacklist? Is it 
> sudo aptitude remove ndiswrapeer blacklist?

---

### Post by ghost_ryder35 on 2008-05-10
> **cosine352 said:**
> How do I remove ndiswrapeer and blacklist? Is it 
?
should work if ndiswrapper is spelled right :)  or you could do it through synaptic package manager
system, administration, synaptic package manager :)

---

### Post by cosine352 on 2008-05-10
Thanks ghost_ryder35. 
I will try it and post my results.

---

### Post by cosine352 on 2008-05-10
I am stuck at the last step

> /broadcom-wl-4.80.53.0/kmod$ ../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory


---

### Post by cosine352 on 2008-05-10
anybody ????? please help

---

### Post by ghost_ryder35 on 2008-05-10
ok so we did
1. [COLOR=#ff0000]sudo apt-get install build-essential[/COLOR]
[COLOR=black]so we can build stuff, then we did[/COLOR]
[COLOR=#ff0000][COLOR=black]2.[/COLOR] wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)[/COLOR]
[COLOR=black]to download the b43-firmware cutter package, then we un tarred it[/COLOR]
[COLOR=#ff0000][COLOR=black]3.[/COLOR] tar xjf b43-fwcutter-011.tar.bz2[/COLOR]
[COLOR=#ff0000][COLOR=black]then we changed directories to the untarred files location[/COLOR]
[COLOR=black]4.[/COLOR] cd b43-fwcutter-011[/COLOR]
[COLOR=#ff0000][COLOR=black]then we issue the make command[/COLOR]
[COLOR=black]5.[/COLOR] make[/COLOR]
[COLOR=black]then we went to our home directory[/COLOR]
[COLOR=#ff0000][COLOR=black]6.[/COLOR] cd ..[/COLOR]
[COLOR=#ff0000][COLOR=black]7.[/COLOR] [/COLOR][COLOR=#000000][COLOR=red]export FIRMWARE_INSTALL_DIR=&#8221;/lib/firmware&#8221;[/COLOR] [/COLOR]
then we downloaded the b43 driver
[COLOR=#ff0000][COLOR=black]8.[/COLOR] wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)[/COLOR]
[COLOR=black]then we un tar the driver[/COLOR]
[COLOR=#ff0000][COLOR=black]9.[/COLOR] tar xjf broadcom-wl-4.80.53.0.tar.bz2[/COLOR]
[COLOR=black]then we changed directories to the driver[/COLOR]
[COLOR=#ff0000][COLOR=black]10.[/COLOR] cd broadcom-wl-4.80.53.0/kmod[/COLOR]
[COLOR=#ff0000][COLOR=black]11.[/COLOR] ../../b43-fwcutter-011/b43-fwcutter -w [/COLOR][COLOR=red]/lib/firmware wl_apsta.o[/COLOR]

---

### Post by cosine352 on 2008-05-10
This is my last output. Is this looks okay? Sorry for my ignorance. 

> ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware
b43-fwcutter version 011

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: ../../b43-fwcutter-011/b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware


---

### Post by ghost_ryder35 on 2008-05-10
> **cosine352 said:**
> This is my last output. Is this looks okay? Sorry for my ignorance.
use this command
[COLOR=#ff0000] ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o[/COLOR]

---

### Post by cosine352 on 2008-05-10
I got this. 
> sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw


One more question. Do I need to do this?
> All you have to do is

1. sudo gedit /etc/modprobe.d/blacklist
2. Change &#8220;blacklist bcm43xx&#8221; to &#8220;#blacklist bcm43xx&#8221;
3. Restart. You should get a restricted driver message.
4. Enable restricted driver
5. Restart and you are good to go

I really appreciate you help.

---

### Post by ghost_ryder35 on 2008-05-10
> **cosine352 said:**
> I got this. 
 
 
One more question. Do I need to do this?
 
 
I really appreciate you help.
nope just reboot, as long as you have blacklisted ndiswrapper and bcm43xx as my previous post instructed

---

### Post by cosine352 on 2008-05-10
It is not working.:confused:

---

### Post by ghost_ryder35 on 2008-05-10
grrr.
try 
```

sudo modprobe b43

```
if that doesnt work post
```

ifconfig
iwconfig
iwlist
lspci (i know I want to see it again ;))

```
p.s. make sure ndiswrapper is fully removed and you have blacklisted it under /etc/modprobe.d/blacklist

---

### Post by cosine352 on 2008-05-10
here it is


> sudo modprobe b43
FATAL: Module b43 not found.


> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:63:1a:84
          inet addr:10.244.16.134  Bcast:10.244.19.255  Mask:255.255.252.0
          inet6 addr: fe80::211:43ff:fe63:1a84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5135405 (4.8 MB)  TX bytes:505500 (493.6 KB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:63968 (62.4 KB)  TX bytes:63968 (62.4 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.153.1  Bcast:172.16.153.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.180.1  Bcast:172.16.180.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.


> iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation

> lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: Trident Microsystems XGI Volari XP5 (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller


---

### Post by ghost_ryder35 on 2008-05-10
well since the first one said FATAL the install of the card didnt go as planned.  perhaps try reinstalling via these steps again
 
 
 
ok so we did
1. [COLOR=#ff0000]sudo apt-get install build-essential[/COLOR]
[COLOR=black]so we can build stuff, then we did[/COLOR]
[COLOR=#ff0000][COLOR=black]2.[/COLOR] wget [[COLOR=#000000]http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2[/COLOR]]("http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2")[/COLOR]
to download the b43-firmware cutter package, then we un tarred it
[COLOR=#ff0000][COLOR=black]3.[/COLOR] tar xjf b43-fwcutter-011.tar.bz2[/COLOR]
[COLOR=#ff0000][COLOR=black]then we changed directories to the untarred files location[/COLOR]
[COLOR=black]4.[/COLOR] cd b43-fwcutter-011[/COLOR]
[COLOR=#ff0000][COLOR=black]then we issue the make command[/COLOR]
[COLOR=black]5.[/COLOR] make[/COLOR]
[COLOR=black]then we went to our home directory[/COLOR]
[COLOR=#ff0000][COLOR=black]6.[/COLOR] cd ..[/COLOR]
[COLOR=#ff0000][COLOR=black]7.[/COLOR] [/COLOR][COLOR=#000000][COLOR=red]export FIRMWARE_INSTALL_DIR=”/lib/firmware”[/COLOR] [/COLOR]
then we downloaded the b43 driver
[COLOR=#ff0000][COLOR=black]8.[/COLOR] wget [[COLOR=#000000]http://downloads.openwrt.org/sources...0.53.0.tar.bz2[/COLOR]]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2")[/COLOR]
then we un tar the driver
[COLOR=#ff0000][COLOR=black]9.[/COLOR] tar xjf broadcom-wl-4.80.53.0.tar.bz2[/COLOR]
[COLOR=black]then we changed directories to the driver[/COLOR]
[COLOR=#ff0000][COLOR=black]10.[/COLOR] cd broadcom-wl-4.80.53.0/kmod[/COLOR]
[COLOR=#ff0000][COLOR=black]11.[/COLOR] ../../b43-fwcutter-011/b43-fwcutter -w [/COLOR][COLOR=red]/lib/firmware wl_apsta.o[/COLOR]

---

### Post by cosine352 on 2008-05-10
I have done 
> well since the first one said FATAL the install of the card didnt go as planned. perhaps try reinstalling via these steps again



ok so we did
1. sudo apt-get install build-essential
so we can build stuff, then we did
2. wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
to download the b43-firmware cutter package, then we un tarred it
3. tar xjf b43-fwcutter-011.tar.bz2
then we changed directories to the untarred files location
4. cd b43-fwcutter-011
then we issue the make command
5. make
then we went to our home directory
6. cd ..
7. export FIRMWARE_INSTALL_DIR=&#8221;/lib/firmware&#8221;
then we downloaded the b43 driver
8. wget [http://downloads.openwrt.org/sources...0.53.0.tar.bz2](http://downloads.openwrt.org/sources...0.53.0.tar.bz2)
then we un tar the driver
9. tar xjf broadcom-wl-4.80.53.0.tar.bz2
then we changed directories to the driver
10. cd broadcom-wl-4.80.53.0/kmod
11. ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o

This is my blacklist and I have removed ndiswrapper
> # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
blacklist ndiswrapper

Now if I do 
> sudo modprobe b43
FATAL: Module b43 not found.


I have not rebooted my computer though.

---

### Post by ghost_ryder35 on 2008-05-10
```

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
 
# replaced by p54pci
blacklist prism54
 
# replaced by b43 and ssb.
blacklist bcm43xx
 
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
 
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
 
[COLOR=red]blacklist bcm43xx[/COLOR]
[COLOR=yellow]blacklist ndiswrapper[/COLOR] 

```
you can remove the redded blacklist bcm43xx as it looks like it is already in your modprobe a few lines above. blacklist ndiswrapper should still be in your modprobe file
I have posted what your modprobe should look like.
```

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
 
# replaced by p54pci
blacklist prism54
 
# replaced by b43 and ssb.
blacklist bcm43xx
 
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
 
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
 
# disable ndiswrapper from loading
blacklist ndiswrapper 

```

---

### Post by cosine352 on 2008-05-10
still (sfter rebooting and changing the modprobe)

> sudo modprobe b43
FATAL: Module b43 not found.

---

### Post by ghost_ryder35 on 2008-05-10
what happens if you
```

cat /var/log/messages | grep b43

```
any output

---

### Post by cosine352 on 2008-05-10
> sudo /var/log/messages | grep b43
sudo: /var/log/messages: command not found

command not found

---

### Post by ghost_ryder35 on 2008-05-10
> **cosine352 said:**
> command not found
sorry forgot the cat (meow :))
should be 
```

cat /var/log/messages | grep b43

```

---

### Post by cosine352 on 2008-05-10
no output

---

### Post by ghost_ryder35 on 2008-05-10
is three a restricted driver for you?
system, administration, hardware drivers

---

### Post by cosine352 on 2008-05-10
There is only one restricted driver and it is in use
(device driver -> software modem)

---

### Post by cosine352 on 2008-05-10
lshw -C network

> *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32


lspci
> 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)

I have done 
> sudo aptitude install b43-fwcutter

(after trying all the things above)

Still no luck. 

any help ????????:confused::confused:#-o

---

### Post by cosine352 on 2008-05-12
Hi everyone
Ok I have done this ([http://ubuntuforums.org/showthread.php?t=475963 ]("http://ubuntuforums.org/showthread.php?t=475963")) again and now my wireless connection is working. 
But I have to say that Ubuntu 7.10 works much much better for my wireless card. In Ubuntu 7.10 I can get signal from my wireless router even from 30 meter away (55%).:guitar:

Ubuntu 8.04 is not that good to integrate with my wireless card. 
Another thing is in Ubuntu 8.04 VPN connection is not working.:mad:

Any help ????????

---

