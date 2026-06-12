---
title: "broadcom BCM57765/57785 sd card slot not working"
date: 2013-10-02
forum: General Help
---

### Post by mabtifro2 on 2013-10-02
didnt work in 12.10, didnt work in 13.04, and still not working in my beta 13.10. my computer is an acer v5-171. sometimes it used to work if the sd card was already inserted on start up. but not its doesnt seem to work ever. in fact, since upgrading to 13.10, the computer doesnt even shut down if there is an sd card in the slot on shut down, it gives me some error till i remove the card, then it shuts down fine. is there any hope???

---

### Post by heysoos on 2013-11-02
Same issue here. Running 12.04, and the sd card reader does not recognize the card. 

Looking at syslog does not reveal much: 

Nov  2 18:59:03 Ubuntu kernel: [ 7282.848244] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
Nov  2 18:59:04 Ubuntu kernel: [ 7283.956276] mmc0: error -110 whilst initialising SD card
Nov  2 18:59:04 Ubuntu kernel: [ 7284.171549] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
Nov  2 18:59:05 Ubuntu kernel: [ 7285.355227] mmc0: error -110 whilst initialising SD card
Nov  2 18:59:05 Ubuntu kernel: [ 7285.574056] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
Nov  2 18:59:06 Ubuntu kernel: [ 7286.777192] mmc0: error -110 whilst initialising SD card
Nov  2 18:59:07 Ubuntu kernel: [ 7287.002716] sdhci: Switching to 1.8V signalling voltage failed, retrying with S18R set to 0
Nov  2 18:59:08 Ubuntu kernel: [ 7288.306155] mmc0: error -110 whilst initialising SD card

And the card reader should be capable of detecting the SDHC, looking at the details: 

From: lspci -v:

02:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 0742
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at e0520000 (64-bit, prefetchable) [size=64K]
    Capabilities: [48] Power Management version 3
    Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

In addition, the SD card can be read without issue from a USB port, using an external card reader. 

I've tried 3 different SD cards, of varying sizes / cabablilities, but so far, have not been able to get Ubuntu to recognize any of them. 

Any helpful pointers..?

---

### Post by mfisch on 2013-11-15
My friend Grant, who does not have an account here, thinks this patch will help you guys:

[https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a](https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a)

---

### Post by mabtifro2 on 2013-11-18
> **mfisch said:**
> My friend Grant, who does not have an account here, thinks this patch will help you guys:

[https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a](https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a)

how do we apply this patch?

---

