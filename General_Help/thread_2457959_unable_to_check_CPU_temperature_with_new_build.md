---
title: "unable to check CPU temperature with new build"
date: 2021-02-13
forum: General Help
---

### Post by isaiah-isaacson on 2021-02-13
hello folks,
upon finishing my build i would like to keep an eye on my cpu  temperature so I installed psensor. problem is under temp1 which says  AMD cpu It shows 0 degrees celcius which is incorrect. No other cores  are shown in temperature monitor either.

mother board is ASUS Pro WS x570-ACE
cpu is amd 5950x running ubuntu 20.04

  

results of 

$ sudo sensors-detect 

below in link
[URL="https://pastebin.com/JkL4wW6W"]https://pastebin.com/JkL4wW6W
[/URL]

results of 

$ watch -n 2 sensors

nvme-pci-0100
Adapter: PCI adapter
Composite:    +38.9°C  (low  =  -0.1°C, high = +69.8°C)
                       (crit = +84.8°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)


And here are my preference settings:
enable support of lm-sensors is check
enable support of NVCtrl(nvidia) is check
enable support of ATI ADL is check(but this text is all grey out)
enable support of gtop2 is check
enable support of hddtemp daemon is uncheck
enable support of libatasmart is uncheck
enable support of udisk2 is check

EDIT SOLVED: [https://askubuntu.com/questions/1164206/lm-sensors-and-amd-ryzen-x570-chipset](https://askubuntu.com/questions/1164206/lm-sensors-and-amd-ryzen-x570-chipset)

 
[URL="https://pastebin.com/JkL4wW6W"]

[/URL]

---

