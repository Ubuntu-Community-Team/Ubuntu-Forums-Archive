---
title: "Help needed with installing a HeadSet"
date: 2019-01-13
forum: General Help
---

### Post by icebear2230 on 2019-01-13
Hello,
Ive bought myself because of the great sound and also because i really needed a new headset a Teufel Cage. (You dont need to know this Company)

so the problem is: The drivers are only aviable for windows. is there any possiblity to convert them to linux?

---

### Post by TheFu on 2019-01-13
Probably not.

If it uses an analog port, then the drivers shouldn't matter.
If it uses a USB port, perhaps there is a fallback model used by all USB audio devices that it can support?
If you can get a copy of the driver source code from Teufel and get them to ship the same headset you have to a linux audio driver developer, perhaps, there is hope.  I wouldn't hold my breath for this one.

If you don't want to be disappointed with hardware, always check for linux compatibility BEFORE you buy.  And for the least hassles, you want to check that the driver is included with the kernel.  Long ago, I picked up a hardware RAID card that had "Linux compatible/Linux Drivers included" on the box.  When I got it home, I found that the drivers were binary, not source, and only worked with a 4 yr old kernel release. No current or newer kernels would be supported.  There were kernel drivers for the card, but not for RAID, just JBOD access.  The same story applies to printers, scanners, USB hubs, and all external peripherals that connect to a computer.

**Check for kernel drivers BEFORE purchase.**

Oh ... and buy Intel Network cards, not the other makers. You'll be much happier for a number of reasons and they are $5 more. How much wasted time, effort, frustration, is $5 more worth to you?

---

