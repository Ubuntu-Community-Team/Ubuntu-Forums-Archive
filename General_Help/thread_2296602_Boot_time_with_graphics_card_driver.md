---
title: "Boot time with graphics card driver"
date: 2015-09-27
forum: General Help
---

### Post by Zain_Ul_Haq on 2015-09-27
[SIZE=2]Hello, I am new to Linux. My laptop came with ubuntu 12.04, i upgraded it to 14.04. The problem is when i use the graphics card driver, it takes up about 25 seconds more than when i boot up with nouveau driver, there is a black empty screen before the splash screen which takes up most of the time. My graphics card is nvidia 820m and the driver i use is nVidia GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M]. My laptop is dell inspiron 3542. Is this normal behavior, does using the graphics driver increase boot time?[/SIZE]

I also want to ask if boot time of 14.04 is greater than that of 12.04 because even without using the graphics driver the boot time of 14.04 is about 10-15 seconds greater than 12.04 on my system.
This is annoying because i know that the system can go faster but i dont know why it is taking this much time. 

I used bootchart to determine the boot times.
Please help.

---

### Post by kc1di on 2015-09-27
Hello Zain_Ul_Haq and Welcome to Ubuntu Forums, 

I noticed a slight increase in boot times when I switched from 12.04 to 14.04 also.  Believe it has to do with the number of kernel modules being loaded at any time.
If I'm not mistake the nouveau driver is in the kernel and the Nvidia driver is loaded as an additional module so that it may indeed increase your boot times. 

If you go to a terminal and type ```
dmesg
``` it will return an output of the last boot session.
it will look something like this. 

```
 0.197520] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.197564] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
[    0.197572] pci 0000:00:08.0: reg 0x10: [io  0xe400-0xe407]
[    0.197575] pci 0000:00:08.0: reg 0x14: [io  0xe080-0xe083]
[    0.197579] pci 0000:00:08.0: reg 0x18: [io  0xe000-0xe007]
[    0.197583] pci 0000:00:08.0: reg 0x1c: [io  0xdc00-0xdc03]
[    0.197586] pci 0000:00:08.0: reg 0x20: [io  0xd880-0xd88f]
[    0.197590] pci 0000:00:08.0: reg 0x24: [mem 0xfbefc000-0xfbefcfff]
[    0.197649] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
[    0.197657] pci 0000:00:08.1: reg 0x10: [io  0xd800-0xd807]
[    0.197660] pci 0000:00:08.1: reg 0x14: [io  0xd480-0xd483]
[    0.197664] pci 0000:00:08.1: reg 0x18: [io  0xd400-0xd407]
[    0.197668] pci 0000:00:08.1: reg 0x1c: [io  0xd080-0xd083]
[    0.197671] pci 0000:00:08.1: reg 0x20: [io  0xd000-0xd00f]
[    0.197675] pci 0000:00:08.1: reg 0x24: [mem 0xfbef7000-0xfbef7fff]
[    0.197740] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
[    0.197766] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197787] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.197820] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
[    0.197845] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197866] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.197899] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
[    0.197923] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.197944] pci 0000:00:0c.0: System wakeup disabled by ACPI
[    0.197978] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
[    0.197984] pci 0000:00:0d.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
[    0.197989] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.197994] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
[    0.197999] pci 0000:00:0d.0: reg 0x30: [mem 0xfbec0000-0xfbedffff pref]
[    0.198059] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.198108] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.198154] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.198200] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.198248] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.198349] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
[    0.198354] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.198356] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.198357] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.198359] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.198361] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xfbffffff] (subtractive decode)
[    0.198362] pci 0000:00:04.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.198392] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.198422] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.198463] pci 0000:04:00.0: [11c1:0630] type 00 class 0x078000
[    0.198478] pci 0000:04:00.0: reg 0x10: [mem 0xfbfff000-0xfbffffff 64bit]
[    0.198543] pci 0000:04:00.0: PME# supported 
```

The numbers in bracketts tell how many seconds into the boot an item is launched.  thus if there is a big gap in the timing , that is where the delay is taking place.
this may reveal to you where the hold up is and you may or may not be able to correct it.

---

### Post by Zain_Ul_Haq on 2015-09-27
Thanx for your help, i did as you said. There seems to be a few time gaps in there but i am not able to decipher these processes. I am attaching the output here, could you please look into it and help me figure out the issue.
[http://pastebin.com/PLPu7agY](http://pastebin.com/PLPu7agY)

---

### Post by kc1di on 2015-09-28
From what I can see from the output , it's the ACPI that's hogging most of the boot time.  So something to do with that. 
But I'm not sure how to speed that up much. 

You may want to install grub customizer and carefully play with it's parameters.  that may speed this up a bit. 
you can find it[ here.]("http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/")

---

### Post by Yellow Pasque on 2015-09-28
There's a sizable time gap here:
```
[   22.766595] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   23.256300] init: nvidia-prime main process (1074) terminated with status 127
[   29.132308] init: plymouth-upstart-bridge main process ended, respawning
[   29.156189] init: plymouth-upstart-bridge main process ended, respawning
[   47.864136] audit_printk_skb: 123 callbacks suppressed
```

I would try disabling plymouth or at least removing 'splash' from the boot line.

---

