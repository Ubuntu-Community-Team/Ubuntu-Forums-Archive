---
title: "Suspend problem"
date: 2012-12-15
forum: General Help
---

### Post by dyrer on 2012-12-15
Hello, and thank you making this great community
I have a problem with suspend, if my computer suspend with my command or with power option, when i press button to start again there is only a cursor blinking.
Also i want to ask you if there any way to make not to suspend if another computer through network wire/wireless is using ubuntu pc.
thanks in advance

---

### Post by Toz on 2012-12-16
Can you provide some more information:

1. The make and model of your computer.

2. Your video card and driver:
```
sudo lspci -vnn | grep -A15 VGA
```

3. The results of this command:
```
cat /proc/cmdline
```

4. The contents of your /var/log/pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by dyrer on 2012-12-16
Graphics Card

02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870] [1002:9440] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Device [1787:2267]
	Flags: bus master, fast devsel, latency 0, IRQ 73
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbbe0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fbbc0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870] [1002:aa30]
	Subsystem: Hightech Information System Ltd. Device [1787:aa30]


linux
BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=d4e73d22-419d-48ba-b534-e67061805f22 ro quiet splash vt.handoff=7


[http://paste.ubuntu.com/1443649/](http://paste.ubuntu.com/1443649/)

---

### Post by Toz on 2012-12-16
What is the make and model of your computer?

Can you try the following to see if they successfully suspend/resume the computer:
```
sudo pm-suspend --quirk-test --quirk-s3-mode
```
```
sudo pm-suspend --quirk-test --quirk-vbe-post
```

Please also post back the contents of your /var/log/pm-suspend.log file after the above 2 attempts:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by dyrer on 2012-12-18
[http://paste.ubuntu.com/1447916/](http://paste.ubuntu.com/1447916/)

---

### Post by Pjotr123 on 2012-12-18
If the problem can't be solved (which is usually the case with suspend), you can always disable suspend entirely:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)

---

### Post by Toz on 2012-12-18
What is the make and model of your computer?

---

### Post by dyrer on 2013-01-22
I bought a new ATI HD 7770 with new drivers and problem solved

---

