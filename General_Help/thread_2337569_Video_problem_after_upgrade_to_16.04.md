---
title: "Video problem after upgrade to 16.04"
date: 2016-09-19
forum: General Help
---

### Post by dfpd62 on 2016-09-19
Hi All.

Just updated to 16.04 from 14.04 and seem to have no video driver for my Radeon hd6450, have been reading that the fglrx driver has been discontinued and replaced with ATIAMD driver which does not seem to be installed/working. display is "Built in Only" and the only video mode avaliable is 1024x768 4:3.

have preformed this command.

dd@dd-desktop:~$ sudo lshw -C video

*-display UNCLAIMED
description: VGA compatible controller
product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list
configuration: latency=0
resources: memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff


have also read that I must not try to reinstall the fglrx driver because it will severely break 16.04.

How can I install a driver that will give back video card functionallity?

Any Help Appreciated

Thanks in advance,, Donald

---

### Post by RobGoss on 2016-09-19
Hello and welcome, Have you try installing the necessary drivers using **software & updates**, choose  **Additional Drives** and let it scan to see what's available

---

### Post by dfpd62 on 2016-09-19
Did that, and lots of other things, got it fixed now, think removing all traces of fglrx and rebooting done the trick.

---

### Post by RobGoss on 2016-09-19
> **dfpd62 said:**
> Did that, and lots of other things, got it fixed now, think removing all traces of fglrx and rebooting done the trick.

Give this **video driver how-to, **page a look they have information about install the different drivers [https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto)

---

### Post by RobGoss on 2016-09-19
> **dfpd62 said:**
> Did that, and lots of other things, got it fixed now, think removing all traces of fglrx and rebooting done the trick.

So is everything working as expected?

---

### Post by ajgreeny on 2016-09-19
> **RobGoss said:**
> Give this **video driver how-to, **page a look they have information about install the different drivers [https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto)

That will not help with 16.04 as the proprietary driver, fglrx, does not work with that version of Ubuntu.
@ dfpd62
I think you did the correct thing by removing all traces of fglrx as that can cause a lot of problems in 16.04; you are stuck with the open source driver that was installed by default when you installed the OS.

---

