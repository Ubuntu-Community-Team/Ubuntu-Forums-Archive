---
title: "ubuntu 14.04 Data Transfer Speed to USB/SD Card Very Slow"
date: 2015-12-21
forum: General Help
---

### Post by Vikas_K_R on 2015-12-21
Hi,
The Data transfer speed between HDD and SD Card/USB starts with over **100 MBPS** and immediately starts decreasing drastically, reaching as low as **800 KBPS** within few seconds. I have observed this on my ***Lenovo G50-30, HP 15AF001AU*** as well as ***Lenovo G470*** laptops. 
Requesting learned community to kindly help.
Many thanks for your attention and time.

---

### Post by XBNCPRk on 2015-12-21
Almost all devices like that will have a built in buffer that operates much the same way RAM does in a computer. Its much faster, but its relatively tiny. It sounds like the flash drives and SD cards are likely whats holding up the transfer speed, not your system. In the terminal, install and run nmon, then choose the d option to display all attached drives, and their relative disk usages. I think you may find that the peripheral you're writing to is overloaded and responsible for the slow write speed.

```
sudo apt-get install nmon
sudo nmon
```

---

### Post by Vikas_K_R on 2015-12-22
Hi,
Thanks XBNCPRK for your kind attention.
I had observed that when I loaded win10 on the laptop, i could transfer 6.2 GB file to the SD card rather very quickly than the time it took when I loaded ubuntu.
I had tried the same SD card by formatting it complete once in FAT32 and subsequently in NTFS but to no difference in speed.
That is how was my observation.
I have installed and run ***nmon*** but, couldn't make out much from it. Apologies, I am a very beginner.
When the initial speed starts at about 160 MBPS, why does it start falling so abruptly, continuously as if I am watching a fuel reading change at a gas station. :-) 
Awaiting your advice.
Thanks.

---

