---
title: "Boot skips GRUB and goes straight to Ubuntu"
date: 2018-07-16
forum: General Help
---

### Post by thedjphd on 2018-07-16
A few days ago, Windows had to restart for an update. I was not around to re-select windows on the restart screen (So it is unknown whether it went to GRUB that time or not). When I restarted the computer, and every time after that, it skips everything. The ACER logo doesn't appear, the computer lags out for a little bit, every now and again flashing some sort of screen (could be GRUB, maybe linux log in), and eventually just jumps straight to Ubuntu. 

I've attempted the Boot Repair software, and have been unsuccessful. 

I'm stuck because I cannot even get into the BIOS.

Please let me know,

James

---

### Post by oldfred on 2018-07-16
UEFI system?
What model Acer, What version Windows & Ubuntu?

You need to get into UEFI/BIOS boot menu and see if you can directly boot Windows  from that.
Grub only boots working Windows. And that is Windows that does not have fast start up or hibernation on. And Windows with updates turns fast start up back on and normally resets itself as first in UEFI boot.

You may need to do a cold boot, or fully shutdown system. If laptop also remove battery.
Remove power plug, hold power on switch to drain all internal power and then boot and immediately press correct key to get into UEFI.

As UEFI has fast boot which is different than Windows fast start up. UEFI fast boot assumes no changes to system, so it does not spend time checking for hardware or software and writing that info to drive for operating system. But then it is so fast you do not have time to press any key.

If you can run Boot-Repair, post link to summary report.
If you are booting using grub, you also may be able to press down arrow key as soon as it starts. Grub will recognize grub menu change and may boot later line. Bottom line in menu is "System Setup" which is switch to UEFI/BIOS.

---

