---
title: "Random VCE init error (-110)"
date: 2015-12-31
forum: General Help
---

### Post by Prescience500 on 2015-12-31
I was playing a game on my computer when the whole system froze. I pushed the button on my computer to restart and it booted to a black screen. A picture of it and the text that appeared is attached. Once it started looping, I took the picture. I'm sure it would have kept going if I let it. Please let me know how I can fix the issue.

[ATTACH=CONFIG]266483[/ATTACH]

No updates have occurred since my last boot. I'm using Kubuntu 15.10. I'm using the open source graphics driver. Everything was working just fine previously. I have not installed any bleeding edge drivers, kernels, etc. Everything is vanilla except for a couple of game apps. My graphics card is an AMD R7 250. I found a similar thread, but unlike the other person, I am unable to boot with the drive with the problem.

 My previous drive works so I've provided terminal output from that in case it's helpful, even though it uses the last version of Kubuntu and is working just fine.

michael@michael-Kubuntu-14:~$ sudo lspci -vnk | grep -iA20 vga
[sudo] password for michael: 
02:00.0 0300: 1002:6610 (prog-if 00 [VGA controller])
        Subsystem: 1682:7250
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fbf80000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at e000 [size=256]
        Expansion ROM at fbfc0000 [disabled] [size=128K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Capabilities: [270] #19
        Kernel driver in use: radeon

02:00.1 0403: 1002:aab0
        Subsystem: 1682:aab0
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
michael@michael-Kubuntu-14:~$ dmesg | egrep -i 'vce|error'
[   11.054785] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.050772] init: Error while reading from descriptor: Broken pipe
michael@michael-Kubuntu-14:~$ uname -a
Linux michael-Kubuntu-14 3.16.0-44-generic #59-Ubuntu SMP Tue Jul 7 02:07:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by sandyd on 2015-12-31
Looks like your drive may be corrupt. 

Boot to a LiveCD, and check the smart status of the drive. Could be that only data on the partition is corrupt, or the drive is failing.

I would recommend taking a copy of the drive via dd/ddrescue from a LiveCD before attempting recovery. See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) if you require recovery methods

---

### Post by Prescience500 on 2016-01-02
Thanks for letting me know the problem. Once I realized I'd have to reinstall things, I was able to get everything up and running again. I'm finding now that I have 20 bad sectors. I think I just got really unlucky in where the sectors went bad.

Should I be worried that the bad sectors are "pending" and "uncorrectable?" That is to say, might it be a problem later? If so, what should I do about it to avoid another failure?

---

