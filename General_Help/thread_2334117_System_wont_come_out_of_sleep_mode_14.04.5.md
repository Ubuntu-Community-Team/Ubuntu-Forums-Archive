---
title: "System wont come out of sleep mode 14.04.5"
date: 2016-08-16
forum: General Help
---

### Post by Wildmanron on 2016-08-16
My problem is i upgraded to the new version of Ubuntu 16.04 and had the same issue of not waking up from sleep mode. So i reinstalled 14.04 cause it had no problems on this system but now it wont wake up from sleep mode ever since i reinstalled. as far as I know the video card is this

ron@ron-MS-7309:~$ sudo lspci -vnn | grep -A12 VGA
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0620]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at e000 [size=256]
    Memory at dfff0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at dffc0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: radeon

ron@ron-MS-7309:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=3a7409b8-30c8-4c59-b759-d62152df7b95 ro quiet splash vt.handoff=7

not sure if this is all you need or not but this is what i got with the commands i found on a google search.

this is an older system i don’t remember what mother board is in it so if you need that kind of info please tell me what command i need to enter to get it to tell me so i can post the results to you. I am still kind of a nu be to this Linux thing I just love the way it runs so much better than windows any day. Thanks for any help you can give me on this matter Ron F.

---

### Post by ron5 on 2016-08-24
Dose anyone think that this has something to do with my usb ports not working when the system is in sleep mode is that why it wont wake up cause it cant see the mouse or key board. but it also doesn’t seem to see the power button being pressed it has to be turned off then back on to use it again. is there any log files or system thing that will tell anyone why it wont wake up. any help would be appreciated.

---

### Post by kansasnoob on 2016-08-24
Which kernel are you using in 14.04.5? Please post the output of:

```
uname -a
```

If it's the lts-xenial kernel it could be a kernel bug shared both by that Trusty HWE and Xenial so it might be worth trying the archived 14.04.1 images with the 3.13 series kernel. About HWE:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

