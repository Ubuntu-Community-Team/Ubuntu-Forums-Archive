---
title: "Ubuntu 18.04 Wi-Fi adapter not found"
date: 2022-09-12
forum: General Help
---

### Post by ksarvin04 on 2022-09-12
Ubuntu ver.: 18.04.6.
Kernel ver.: 5.4.0-126-generic.
Laptop model: Intel(R) Core(TM) i7-1065G7 CPU @ 1.30GHz.
Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31).
GRUB Dual-boot with Windows 10. 

The system says that the Wi-Fi adapter was not found despite the fact that the "lspci | grep -i wireless" sees the adapter itself. 
This happened after a kernel update about six months ago. I tried many methods described on the Internet but wasn't be able to restore Wi-Fi.:(

Help please.

---

### Post by miguel001 on 2022-09-12
I've seen Linux issues sometimes take a year or longer in really rare cases. Some issues make me jump distros rofl :)

You could try looking for a separate driver install maybe. Supposedly from this link they say you can contact Qualcomm and get a driver from them for the QCA9377 as they for some reason aren't posting it on their website [URL="https://developer.qualcomm.com/forum/qdn-forums/hardware/qca9377/68344"]https://developer.qualcomm.com/forum/qdn-forums/hardware/qca9377/68344

[/URL]Its possible for hardware to show up and yet not have a driver installed. I've seen this with my Bluetooth adapter. After a few hours I debugged it as needing a driver.

You could also work around it by buying a different branded chipset via usb. One that's more compatible. With the right USB and adapter USB spec you can achieve very high transfer rate likely even equaling the ac you have there if not besting it.

---

