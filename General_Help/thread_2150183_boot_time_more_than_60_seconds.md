---
title: "boot time more than 60 seconds"
date: 2013-05-31
forum: General Help
---

### Post by curiousgally on 2013-05-31
All,

I have clean installed ubuntu 12.10. I have an SSD and BIOS is setup in AHCI mode. It takes more than a minute to boot. When I select Compatability mode instead of AHCI mode it boots in less than 20 seconds. What could be the issue. Since I have window8 on another drive which is in AHCI mode(and doesn't boot in Compatability mode) I dont want the hassle of switching in BIOS everytime I want to boot to windows. 

Any help is appreciated !!!

Thanks.

---

### Post by curiousgally on 2013-05-31
I see this to be the issue from dmesg file:


> 1.806904] usb 1-1.6: >Manufacturer: Chicony Electronics Co., Ltd.
[    5.952855] ata2: link is slow to respond, please be patient (ready=0)
[   10.593941] ata2: COMRESET failed (errno=-16)
[   15.946074] ata2: link is slow to respond, please be patient (ready=0)
[   20.587063] ata2: COMRESET failed (errno=-16)
[   25.939195] ata2: link is slow to respond, please be patient (ready=0)
[   55.574964] ata2: COMRESET failed (errno=-16)
[   55.574974] ata2: limiting SATA link speed to 1.5 Gbps
[   55.894602] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)


and it looks very similar to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991040") bug.

Any inputs to debug this?

---

