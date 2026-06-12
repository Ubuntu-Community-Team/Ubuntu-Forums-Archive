---
title: "Boot hang at &quot;starting up&quot;"
date: 2006-12-17
forum: General Help
---

### Post by Stex on 2006-12-17
On booting ubuntu edgy, before the splash screen appears, everything will pause for ~10 seconds after grub has gone through and the words "Starting Up" have been displayed. After this an error message is shown for a split-second before the splash appears and everything boots normally.

> [17179588.320000] PCI: Cannot allocate resource region 0 of device 0000:05:00.0

Originally I thought this error was the source of the hang but after looking through syslog I doubt this as the times shown for many lines before and after this error are stamped in the same second. There isn't anything in syslog before this section that goes for over a second so I presume whatever is causing the hang happens before the logging starts.

I installed bootchart, and have attached a chart from it, which shows a lag of time about right for my problem in khelper and kthread. Or maybe the problem is in init. Thing is, I have no idea what to do now that I've -maybe- found the problem.

I'm presuming this kind of hang isn't normal as I have another laptop running edgy which gets past this "Starting Up" stage in less than a second.

Can anyone help or at least point me to a bug report so I know this is being fixed sometime? Adding 15 seconds onto an already 45 second boot just isn't good at all.

- Thanks



**Section of syslog around the error**
> Dec 17 19:46:23 LappyJr kernel: [17179588.320000] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] pnp: PnP ACPI init
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] pnp: PnP ACPI: found 11 devices
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] PnPBIOS: Disabled by ACPI PNP
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] PCI: Using ACPI for IRQ routing
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] PCI: Cannot allocate resource region 0 of device 0000:05:00.0
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
Dec 17 19:46:23 LappyJr kernel: [17179588.320000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0

---

