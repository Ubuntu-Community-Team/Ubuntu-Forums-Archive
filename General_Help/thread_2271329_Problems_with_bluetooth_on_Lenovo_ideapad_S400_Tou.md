---
title: "Problems with bluetooth on Lenovo ideapad S400 Touch on ubuntu 14.04"
date: 2015-03-29
forum: General Help
---

### Post by ivan_omar on 2015-03-29
Hi guys ):P
I have a problem with my bluetooth, when i try to conect any device with my computer, i search for devices, but anything happens, and it's the same wen i try to conect any device with my computer searching with my device.

i tried with blueman and with another post that says that i should try reinstalling ```
"linux-headers-generic build-essential"
```   [http://ubuntuforums.org/showthread.php?t=2251009](http://ubuntuforums.org/showthread.php?t=2251009)

this is one of the images that i took 
[IMG]https://farm8.staticflickr.com/7602/16780919949_263d0da747_s.jpg[/IMG]

---

### Post by jeremy31 on 2015-03-29
Open terminal and post the results from this command ```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all
```

I am still not sure how installing wifi backports worked in the linked thread, but I know why the last posters wifi quit working

---

### Post by ofpprieto on 2015-11-07
hi this is the result:
> 01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:3977]
	Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Lenovo Device [17aa:3218]
	Kernel driver in use: ath9k
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bash: rfkill: no se encontró la orden





---

### Post by jeremy31 on 2015-11-07
That one should be supported.  Post ```
modinfo ath3k | grep 3004; ls /lib/firmware/ar3k/; rfkill list all
```

---

