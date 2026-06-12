---
title: "Slow network performance on Ubuntu Desktop 12.10"
date: 2013-02-11
forum: General Help
---

### Post by RottenMutt on 2013-02-11
i running Ubuntu Desktop 12.10 (Quantal) and have slow network performance 40-50 MB/s that i'm blaming on my network drivers.  Transfer speed is about half the network capability, my old core 2 MB could get 100MB/s.  My new motherboard is a Gigabyte GA-Z77X-UD5H with a Intel i5-3450S CPU @ 2.80GHz with 16GB of ram.
I'm using the Intel e1000e controller for my lan, and the 3Com for my internet connection.  Can't even get the Atheros chip to work.  Files are on a software Raid 5 array with 6x 2TB harddrives.

$ lspci | grep Eth
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
04:00.0 Ethernet controller: 3Com Corporation 3CR990-TX-97 [Typhoon 168-bit] (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)

$ dmesg | grep e1000
[    1.219807] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    1.219809] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.219840] e1000e 0000:00:19.0: setting latency timer to 64
[    1.219894] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.219921] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    1.476218] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 90:2b:34:da:f5:34
[    1.476220] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.476252] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   17.645443] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   17.747372] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   21.306309] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx


If anyone has any ideas i'm game...
thanks eric

---

### Post by codemaniac on 2013-02-11
Hi RottenMutt,

Your post is now moved to its own thread.

Cheers!!

---

### Post by RottenMutt on 2013-02-15
anyone have any ideas why the Intel Corporation 82579V Gigabit Network driver is so slow?

i've tried the Atheros AR8161 Gigabit Ethernet without luck as well, plus the package even broke the intel driver.

i'm going to try the driver from intel e1000e-2.2.14

---

### Post by RottenMutt on 2013-02-16
Is there some sort of bandwidth rule in place, bandwidth is limited to 250 Mbps' or one fourth of Gb eithernet.

---

### Post by RottenMutt on 2013-02-17
well i gave up and installed ClearOS and am getting real fast file transfers now ~100MB/s.  plus i can set whatever class network i want for ics.

something in ubuntu is throttling samba or network speed, perhaps so the desktop stays snappy.

---

