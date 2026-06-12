---
title: "Questions about RAID 0"
date: 2007-01-01
forum: General Help
---

### Post by solarwind on 2007-01-01
Hi everyone, I have a few questions about RAID 0.

I am planning to hook up 2 identical 80 GB SATA drives as RAID 0. My ASUS M2NBP-VM motherboard has a built-in hardware RAID system by NVIDIA.

If I hook up my drives as RAID 0:

1) Will Windows see it as 1 drive and treat it like 1 drive and install normally?
2) Will Kubuntu see it as 1 drive and treat it like 1 drive and install normally?
3) Would I need any drivers? (It's all hardware RAID which is built-in into the motherboard).

---

### Post by PilotJLR on 2007-01-01
No, you don't have true hardware RAID... the raid built into desktop boards is what some people call "fake" raid. The RAID functionality is achieved through a Windows driver (F6 on install, that thing) and the driver offloads actual raid operations to the CPU.

So, both WIndows and Linux will be aware that the computer has 2 physical drives, though with the Windows driver, you will only be presented with 1 logical drive. A similar setup is possible with the software RAID that comes with pretty much any Linux system.

A true hardware RAID system usually requires a server grade PCI-X card and often costs upwards of $400; cards such as this will present 1 drive to the OS. Even the $100-ish PCI "raid" cards you can buy are "fake" raid.

---

### Post by solarwind on 2007-01-12
> **PilotJLR said:**
> No, you don't have true hardware RAID... the raid built into desktop boards is what some people call "fake" raid. The RAID functionality is achieved through a Windows driver (F6 on install, that thing) and the driver offloads actual raid operations to the CPU.

So, both WIndows and Linux will be aware that the computer has 2 physical drives, though with the Windows driver, you will only be presented with 1 logical drive. A similar setup is possible with the software RAID that comes with pretty much any Linux system.

A true hardware RAID system usually requires a server grade PCI-X card and often costs upwards of $400; cards such as this will present 1 drive to the OS. Even the $100-ish PCI "raid" cards you can buy are "fake" raid.


Aww ****! Hmm. Oh well, I still got a pretty good motherboard though. But the manufacturers should mention that the onboard RAID is not really true hardware RAID.

---

### Post by PilotJLR on 2007-01-12
If you use the RAID tools in linux, the raid performance will be at least as good as (if not better) than using the vendor driver in Windows...
So setup is just slightly more complicated, but it still pays off!

---

### Post by dcstar on 2007-01-13
> **solarwind said:**
> Hi everyone, I have a few questions about RAID 0.

I am planning to hook up 2 identical 80 GB SATA drives as RAID 0. My ASUS M2NBP-VM motherboard has a built-in hardware RAID system by NVIDIA.
.........

You are aware that RAID 0 doubles the potential chance of failure because if one of your drives dies, you lose **ALL** of your data.

You'd be much better off having two separate filesystems.

---

### Post by solarwind on 2007-01-27
> **dcstar said:**
> You are aware that RAID 0 doubles the potential chance of failure because if one of your drives dies, you lose **ALL** of your data.

You'd be much better off having two separate filesystems.

You are aware that the hard drive is the worst bottle neck in a computer system. Improving the speed will greatly improve performance.

---

### Post by dcstar on 2007-01-27
> **solarwind said:**
> You are aware that the hard drive is the worst bottle neck in a computer system. Improving the speed will greatly improve performance.

And exactly how does RAID-0 achieve that?

As far as determining what "bottlenecks" affect system performance, that depends greatly on the hardware configuration and the application demands placed on an individual system.

For example, someone may have a PC with not quite enough memory, and have a RAID-0 setup with the Swap area spread across two physical drives - or even with directory space on one drive, and actual data area on another drive.

Then all writes to Swap will incur data writes to two physical drives, which on most systems will incur greater overheads than a system with the swap space all on one physical drive.

---

### Post by technoplume on 2007-01-27
Well first of HD are not bottleneck device, Bottleneck mean that the quantity of information that come in is more that the device can deliver. As an exemple, an 5 line highway whit high trafic comming in a 2 line road. You can see this whit videocard using the PCI slot.

In the case of HD, there acces time is to slow so the CPU has to wait and lose clock cycles waiting for information. In a raid 0 setup, the system will read both HD at the same time, cutting on acces speed and improving the quantity of information flow to the CPU and ganing some lost clock cycle.

---

### Post by solarwind on 2007-01-28
Yeah. Please don't give me layman's terms. It's just *lame*. For the average user and especially power users, raid 0 will speed up the system a lot. For example, startup will be much faster and application launching will be much faster. Trust me, I've evaluated the differences before. 

One question, where do I get the nVidia raid drivers for Linux and when and how do I install them?

---

### Post by PilotJLR on 2007-01-28
Wow dude, that's a little harsh. Especially considering your question.

The driver used by "fake raid" systems like the nvidia one (I have the an nvidia 4 myself) are just means to trick Windows into performing software raid. So, to answer your question, this driver for linux does not exist.

Instead, setup a software raid 0 with the tools you already have. The performance will be exactly the same as if you F6'd a windows installation and used a windows raid driver, cause this accomplishes the same thing.

Read this carefully:
[http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.5](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.5)

You basically need to make a single md device from 2 physical devices... and it's done.

> **solarwind said:**
> Yeah. Please don't give me layman's terms. It's just *lame*. For the average user and especially power users, raid 0 will speed up the system a lot. For example, startup will be much faster and application launching will be much faster. Trust me, I've evaluated the differences before. 

One question, where do I get the nVidia raid drivers for Linux and when and how do I install them?

---

### Post by solarwind on 2007-01-29
> **PilotJLR said:**
> Wow dude, that's a little harsh. Especially considering your question.

The driver used by "fake raid" systems like the nvidia one (I have the an nvidia 4 myself) are just means to trick Windows into performing software raid. So, to answer your question, this driver for linux does not exist.

Instead, setup a software raid 0 with the tools you already have. The performance will be exactly the same as if you F6'd a windows installation and used a windows raid driver, cause this accomplishes the same thing.

Read this carefully:
[http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.5](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.5)

You basically need to make a single md device from 2 physical devices... and it's done.

But then if it's software raid, why does the motherboard have to anything with "RAID" at all? (since it's all software)?

---

### Post by Nachtengel on 2007-01-29
I ran into the same problem on my ASUS A8N-SLI Deluxe motherboard.  What was referred to as "software RAID" or "fake RAID" is really some software flashed onto the "fakeRAID" controller chip.  The firmware on this chip is designed to work with a windows driver to give the RAID performance.  I ended up using linux's ability to run a software RAID without general hardware, but to do so I had to turn the RAID chip on my motherboard off in my BIOS.  This makes the motherboard ignore the chip with the windows-centric firmware.

---

