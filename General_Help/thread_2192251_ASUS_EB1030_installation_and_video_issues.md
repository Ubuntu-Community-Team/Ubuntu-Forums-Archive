---
title: "ASUS EB1030 installation and video issues"
date: 2013-12-06
forum: General Help
---

### Post by DuckHook on 2013-12-06
Hi everyone,

It's been a while since I've wrestled with such a cussed install. I now have a working system, but am hoping someone has run across some of these issues and can point me to solutions for some niggling residual problems.

I recently got an [ASUS EB 1030]("http://www.asus.com/us/Commercial_Desktops/EeeBox_PC_EB1030#specifications") and decided to position it for use as a lightweight multifunction household server. I decided the best approach would be to install Ubuntu mini on it, so I repartitioned and installed. Turns out that the EB 1030 has dual Atom processors that are only recognized as i686s, so would only take 32-bit. That wasted my first hour and led to my first problem:

1. Ubuntu 12.04 install process stalls at app loading phase. Network is recognized nicely and mirror is properly assigned but installation stalls going into app loading. I can <Ctrl>+<Alt>+<Fn> to a busybox console to power down properly, but can't get the install to go forward. My solution was to install 13.10, which does not stall. However, for server use, I want an LTS. I may just wait for 14.04 now that I have a working system, but has anyone run into this issue with this HW and if so, how did you solve it?

2. The 13.10 install did not proceed smoothly. Firstly, I wrestled unsuccessfully with a GPT partition, and eventually had to fall back to an MBR partition. Then, GRUB would not install necessitating a post-install fix using boot repair. Upon reboot, GRUB came up properly, but OS loaded without monitor signal which promptly put the monitor to sleep. Fortunately, I had selected ssh-server as an install component and could ssh into the new system. Following [this]("http://ubuntuforums.org/showthread.php?t=2073727") thread, I blacklisted the gma500_gfx driver and now have a working TTY, presumably falling back to a VESA driver. None of the suggestions in [post #11]("http://ubuntuforums.org/showthread.php?t=2073727&page=2&p=12554736#post12554736") of aforementioned thread works. I was not at all impressed. Question: what is the proper video module? How do I get video working in case I want to load X?

3. The Atom D2550 has 2 cores, each with 2 threads. *lshw* shows 1 core disabled, yet 4 "logical" CPUs which implies all 4 threads working. All of *htop*, [Ilscpu[/I], *nproc* and *cat /proc/cpuinfo* shows 4 virtual CPUs as well, so I'm not too concerned, but I am confused why *lshw* is anomolous.

On paper the EB1030 is a slick, light little thing with no moving parts, mountable on your monitor, and sips less than 30 watts at full CPU load. However, it's more trouble than it's worth. Documentation is nonexistent, Googling for info is sparse and uninformative, and the web site sucks. I spent more than a day wrestling with the cursed thing. Can't imagine how a general Linux user could figure it out or put up with it.

Following are HW specs and outputs from various queries:

Model: ASUS EB 1030
CPU: Atom Cedar Trail dual core D2550
SSD: 32 GB
RAM: 2 GB
GPU: Integrated Atom D2xxx/N2xxx graphics
```
DuckHook@piece_of_junk:~$ lspci -vnnk
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf3] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be2] (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at f0e0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84f5]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at dff00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dfd00000-dfdfffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80800000-809fffff
    Prefetchable memory behind bridge: 0000000080a00000-0000000080bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at f080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at f060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at f040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at f020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at dff05000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f000 [size=16]
    Memory at dff04000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
    Flags: medium devsel, IRQ 5
    I/O ports at 0800 [size=32]

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84cd]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at e000 [size=256]
    Memory at dfe04000 (64-bit, prefetchable) [size=4K]
    Memory at dfe00000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at dfd00000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at dfd80000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
``````
DuckHook@piece_of_junk:~$ sudo lshw -sanitize -C processor
[sudo] password for DuckHook: 
  *-cpu:0                 
       description: CPU
       product: Intel(R) Atom(TM) CPU D2550   @ 1.86GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.6.1
       serial: [REMOVED]
       slot: CPU 1
       size: 1865MHz
       capacity: 1865MHz
       width: 64 bits
       clock: 533MHz
       capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 xtpr pdcm movbe lahf_lm arat dtherm
       configuration: cores=2 enabledcores=1 id=1 threads=2
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
     *-logicalcpu:2
          description: Logical CPU
          physical id: 1.3
          width: 64 bits
          capabilities: logical
     *-logicalcpu:3
          description: Logical CPU
          physical id: 1.4
          width: 64 bits
          capabilities: logical
  *-cpu:1 DISABLED
       description: CPU [empty]
       physical id: e020
  *-cpu:2 DISABLED
       description: CPU [empty]
       physical id: e00f
  *-cpu:3 DISABLED
       description: CPU [empty]
       physical id: 1e
  *-cpu:4
       physical id: 2f
       bus info: cpu@1
       version: 6.6.1
       serial: [REMOVED]
       size: 1850MHz
       capabilities: ht
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          capabilities: logical
     *-logicalcpu:2
          description: Logical CPU
          physical id: 1.3
          capabilities: logical
     *-logicalcpu:3
          description: Logical CPU
          physical id: 1.4
          capabilities: logical
``````
DuckHook@piece_of_junk:~$ sudo lshw -sanitize -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:dfc00000-dfcfffff ioport:f0e0(size=8)
```

---

### Post by DuckHook on 2013-12-07
Bump.

---

### Post by DuckHook on 2013-12-08
I managed to solve one mystery at least: it seems that the mini.iso image is incapable of installing to GPT/UEFI. It lacks the needed drivers and install structure. Info [here]("https://help.ubuntu.com/community/Installation/MinimalCD") under "Note". If you want a minimal install on a GPT/UEFI system, you have to use the alternate.iso; not the mini.iso.

I'll just settle for the old MBR/BIOS structure and make the change once 14.04 is released.

---

### Post by Yellow Pasque on 2013-12-09
Ubuntu 12.04.1 would be best, because at least then, you could use the cedarview driver instead of vesa driver: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)

It's hard to say what causes the 12.04 install to fail without a ubiquity log or more info.

As you've come to discover, cedarview graphics are terrible for Linux. Return the box if you can...

---

### Post by DuckHook on 2013-12-09
Thanks Temüjin,

Another mystery solved.> **Temüjin said:**
> It's hard to say what causes the 12.04 install to fail without a ubiquity log or more info.I doubt that any log was generated. The install process stalls before the HDD is written to. I didn't bother trying to chase it down further once 13.10 worked. If 14.04 fails in the same way, I'll be sure to do the diagnostics and post here.> As you've come to discover, cedarview graphics are terrible for Linux. Return the box if you can...Not returnable as it came to me as a hand-me-down. But I'll be okay with VESA. I'm using it as a server box, which was the whole point in the mini.iso, so a crippled driver is not a deal breaker. I just wanted the option of repositioning it should the fancy strike me.

Thanks again for the solution and the link. Who knows? Maybe the cussed thing will get a properly working driver in 14.04.

Good luck with school, certifications and work. Cheers!

—EDIT—

I'm marking this thread solved even though it isn't, really. But sometimes there is no solution and an answer will have to do.

—EDIT 2016-05-30—

I came across this old thread while trying to solve the ongoing video problem with Cedarview graphics and since a Google search sometimes coughs it up, I thought I might update it for the benefit of future troubleshooters.

Cedarview graphics continue to be a thorn in the side of Linux users across all distros, but the landscape is now looking a little less grim. First, some background:

Intel outsourced the video component of some of their Atom-based mini-ATX boards to an outfit called PowerVR. PowerVR refuses to release the specs or details of their video subsystem to the community, and Intel can't release them either because they have only limited rights to the video subsystem. Therefore, it is impossible for the community to write an open-source video driver for any Atom-based box that comes bundled with PowerVR video. However, PowerVR did write an opaque closed-source and wholly-proprietary Linux driver called Cedarview, but this driver is buggy, hobbled, limited to 32-bit architecture and is, frankly, lousy. Moreover, in its first iteration, it was limited to working only with older versions of X and the 3.2.x kernel. This was the state of affairs that existed when I originally created this thread. This background info was unknown to me at the time and has only come to light with subsequent research.

The good news is that the Cedarview driver has now been updated to work with current kernels and versions of X. I was able to install Lubuntu onto my ASUS EB 1030 after a lot of blood, sweat and tears.

The bad news is that the Cedarview driver is still a piece of junk. It is still as buggy, hobbled and limited as ever, and *will not work properly with many monitors*. This last is important and will save you a ton of pain if you understand its limitations and make allowances for it.

Specifically, the driver will probe for monitor characteristics at boot and ham-handedly put some monitors into permanent poweroff mode. Turning ACPI off as a kernel parameter won't work, nomodeset won't work, nothing I've tried works, except to blacklist Cedarview and fall back to VESA. For use as a command-line server, this is not a problem. However, the installation process automatically installs Cedarview, and the first time you boot, you will be blind unless you had the foresight to install ssh server with your initial installation. You can also blacklist the Cedarview driver by placing a command-line option into GRUB at boot, but now we are talking serious geek-fu. The *best* option turns out to be: use an older more primitive monitor with this box if you have one lying around.

If the driver does not put the monitor into permanent poweroff, then it actually manages to display a pretty decent X session. On my EB 1030, Lubuntu runs smoothly. You won't be playing games or doing 3D modelling on the thing, but then, Atom-based computers were not designed for that sort of use in the first place.

A few further caveats:

[LIST=1]
[*]You are restricted to a 32-bit architecture. There is no 64-bit version of the Cedarview driver.
[*]On my EB 1030, a phantom LVDS-0 screen is detected. This likely means that my MOBO was originally designed for netbooks and has an active laptop connector installed that was never disabled. My primitive BIOS lacks the ability to disable video connections (or ACPI for that matter) and no combo of xrandr commands could be made to turn it off either.
[*]The solution is to add:```
video=LVDS-1:d
```...to kernel parameters in GRUB (i.e. "quiet splash video=LVDS-1:d") so that the phantom monitor is disabled in the kernel. As if things were not confusing enough, please note that xrandr reports the phantom monitor as LVDS-0 whereas the actual device name is LVDS-1. Actual device name can be found with:```
ls -la /sys/class/drm
```
[*]Switching to a console with <Alt>+<Ctrl>+<Fn> will not work at all on some monitors. You will just get a blank screen. On others, it will not give you full native resolution, but only XGA.
[*]Within X, forcing apps into full screen mode (typically using the <F11> key) will lock you into XGA resolution if you are lucky, or scramble your monitor output and start overheating it if you are unlucky. Best to avoid full screen mode.
[*]It's a Mickey Mouse graphical system no matter what, so stay away from Ubuntu. Lubuntu runs fine, Xubuntu might be fine too, but avoid anything requiring 3D.
[/LIST]
That's about it. This one was like wrestling a gorilla. But I've invested so much time and effort by now into the cussed thing that I've developed a bloody-minded obsession to triumph over it.

---

