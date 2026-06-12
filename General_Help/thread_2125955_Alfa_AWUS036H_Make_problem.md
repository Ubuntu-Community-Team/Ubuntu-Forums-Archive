---
title: "Alfa AWUS036H Make problem"
date: 2013-03-15
forum: General Help
---

### Post by narfcakes on 2013-03-15
[COLOR=#000000][FONT=Verdana]Hi. I'm trying to get my Alfa AWUS036H working with Chrubuntu (Ubuntu 12.04 LTS on top of ChromeOS), and am having a lot of trouble. I've googled and found quite a few solutions, but none of them have worked. I'm running an Acer C7. Any help would be greatly appreciated. Here's my info I've collected:

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]There's a common error when I try to install any type of driver for it, which is[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]```
make: *** /lib/modules/3.4.0/build: No such file or directory. Stop.
make: *** [all] Error 2
```

I can't even install, it gives me that when I sudo make.

I went into that directory, and this is what build links to:

build -> /build/x86-mario/tmp/portage/sys-kernel/chromeos-kernel-3.4-r996/work/chromeos-kernel-3.4/build/x86-mario

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Here's dmesg's output when I connect the adapter:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]```
[ 1549.448704] usb 2-1.4: new high-speed USB device number 5 using ehci[I]hcd
[ 1549.540769] usb 2-1.4: New USB device found, idVendor=0bda, idProduct=8187
[ 1549.540780] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1549.540787] usb 2-1.4: Product: RTL8187_Wireless
[ 1549.540792] usb 2-1.4: Manufacturer: Manufacturer_Realtek_RTL8187[/I]
[ 1549.540797] usb 2-1.4: SerialNumber: 00C0CA6B5F44
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]lsusb's output:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04ca:3006 Lite-On Technology Corp.
Bus 001 Device 004: ID 064e:d251 Suyin Corp.
Bus 002 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
```

[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]The card isn't listed under ifconfig -a. So, obviously my laptop is recognizing it being connected, but can't use it.

I found [this]("http://ubuntuforums.org/showthread.php?t=2017563") thread today, and it sounds like I'm screwed unless I can somehow get ChromeOS' kernel headers/sources (I have no idea what to do with them). Is there a way to compile while NOT using the 3.4.0 kernel? There are two other folders listed under /lib/modules/ which are 3.2.0-23-generic and 3.2.0-24-generic.

I am desperate, I received this laptop as a gift and would really like to get it working.  I have a feeling the default ChromeOS won't ever be able to support the AWUS036H, and I require it to use my wireless.  Thanks for any responses![/FONT][/COLOR]

---

