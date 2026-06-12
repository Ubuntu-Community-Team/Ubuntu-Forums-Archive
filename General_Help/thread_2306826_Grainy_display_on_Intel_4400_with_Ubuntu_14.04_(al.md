---
title: "Grainy display on Intel 4400 with Ubuntu 14.04 (also 15.10)"
date: 2015-12-19
forum: General Help
---

### Post by SevenKeNz on 2015-12-19
Hi,

I'm using Ubuntu 14.04 and 15.10 on HP ProOne 600 with Intel Graphic HD 4400.

My screen looks grainy as the picture. 
I am also dualbooting with Win 8.1 x64 and the screen is fine on that side.

 [ATTACH=CONFIG]266245[/ATTACH][ATTACH=CONFIG]266246[/ATTACH][ATTACH=CONFIG]266247[/ATTACH]


I have tried installing Intel Graphic Driver from the 01.org site but it didn't seem to work (grainy still.)
I have also tried to other linux distribution (eg. Fedora 23.10 and several other ubuntu based like xubutu and Mint) 
but none seemed to make any difference

When using 'nomodeset' in grub the screen seemed ok but I was stuck with 1024x768 resulution (the native res is 1920x1080)
Is there anything I am missing here? Your advice will be greatly appreciated.

Thank you,

Ken

ps. below is the hardware info regarding the VGA

-------

```
> lshw -c video
*-display                      description: VGA compatible controller
       product: 4th Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```

---

### Post by cjohnsonnucc on 2016-01-05
We just finished troubleshooting the same problem on three ProOne 600's.  Here's what we know so far:
1)  The previous generation ProOne 600 with the i5-4670s processor and fixed monitor stand is unaffected by the problem, even though both appear to have identical video chipsets (detected as Intel i915).
2)  x86 installations of 15.10 work perfectly.  The problem is specific to x64.
3)  As the OP suggested, nomodeset does fix the video quality but leaves one of two problems.  You will either be locked in at 1920x1080 and no hardware acceleration (the system slows to a crawl) or some lower non-native resolution with reasonable performance.  Never did figure out what caused one system to demonstrate the first behavior and another the second.  We tried adding and removing the intel 1.2.1 driver package and every other thing that came to mind.
4)  External monitors work fine while the local video display is grainy.  Without touching /etc/default/grub and adding 'nomodeset', you can connect an external screen on the DisplayPort connector and get perfect video there while it's miserable on the local display.

---

