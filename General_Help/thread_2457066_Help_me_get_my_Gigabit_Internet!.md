---
title: "Help me get my Gigabit Internet!"
date: 2021-01-25
forum: General Help
---

### Post by lsutiger on 2021-01-25
Our company recently upgraded our internet to GB fiber. I have tested on several machines(Windows) on the network and those are getting GB speeds. But my Linux machine is only getting 350Mb. I have done the troubleshooting steps of eliminating the cable being at fault and also the switch which I am connected( other machines on same switch are getting GB speeds).
Here's my  info:
OS - Ubuntu 16.04 64bit
Proc: AMD AMD Phenom(tm) II X4 955
Mem: 16GB PC3-10600
Storage: PNY CS1311 120GB SSD
Net: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
Network Driver: /sys/bus/pci/drivers/r8169/0000:02:00.0

What else can I do to troubleshoot?

---

### Post by ActionParsnip on 2021-01-25
[https://www.cablefree.net/wireless-technology/maximum-throughput-gigabit-ethernet/](https://www.cablefree.net/wireless-technology/maximum-throughput-gigabit-ethernet/)

You won't get 1GB/s sec. There are frame headers and interframe gaps. Also, no transmitter will saturate the connection 100% so the actual speed you will get is about 121MB/s (note capital "B" for bytes, not lower case "b" for bits. This is important). 

What speeds are you seeing in Linux?

---

### Post by lsutiger on 2021-01-25
350 Mb

---

