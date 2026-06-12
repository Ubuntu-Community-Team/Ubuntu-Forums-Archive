---
title: "Brightness controls are not working in sony vaio with amd radeon hd 7650"
date: 2013-01-24
forum: General Help
---

### Post by imankurpatel000 on 2013-01-24
I have a sony vaio SVE15116EN with amd radeon hd 7650 graphics card. I  am currently using ubuntu 12.10. My brightness controls are not working  but sound controls are working fine. I have also tried proprietary  drivers also but no luck. I have tried controlling brightness with  terminal but it also did not work. Please can anyone tell me what can i  do? I have been searching for the solution almost for a week. Any ideas?

---

### Post by Toz on 2013-01-24
Hello and welcome to the forums.

Can you post back the results of the following command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

Also, have you tried the following kernel boot parameter: **acpi_backlight=vendor**? More info on how to temporarily test it is located [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

---

### Post by hokori on 2013-02-09
I am having the same problem.

Here is my output from running that command:

```

/sys/class/backlight/acpi_video0
100
100
100

```

I am using a Sony Vaio E Series 11" with Ubuntu 12.10.  Here is my output from running ```
sudo lspci -vnn | grep -A12 VGA
```

```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9808] (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:90ad]
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

```

---

### Post by Toz on 2013-02-09
Hello hokori and welcome to the forums.

I notice that you are using the open source radeon video driver. Have you tried installing the proprietary AMD driver? You can find it in the Software Centre, select Edit->Sources then look on the "Additional Drivers" tab.

---

