---
title: "Audio not working on Ubuntu 18.04"
date: 2019-09-08
forum: General Help
---

### Post by ericsong1911 on 2019-09-08
Hello! I have Ubuntu 18.04 installed on a Lenovo C630 Yoga Chromebook, and I am having audio issues. For one, I only have a dummy output shown in audio settings, and no audio will play. My speakers never worked on this device. Nothing is detected when I plug in headphones into the headphone jack. 

lspci:
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #3 (rev 21)
00:19.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #2 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1e.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO SPI Controller #0 (rev 21)
00:1e.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO SPI Controller #1 (rev 21)
00:1e.4 SD Host controller: Intel Corporation Device 9d2b (rev 21)
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Multimedia audio controller: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.5 Non-VGA unclassified device: Intel Corporation Device 9d24 (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 7265 (rev 61)
```

Any help would be greatly appreciated!

---

### Post by mörgæs on 2019-09-10
Hi, welcome to the fora.

For hardware this new I suggest that you try 19.10 (under development) in a live boot to see if there is any difference.

---

