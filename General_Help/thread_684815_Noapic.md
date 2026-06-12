---
title: "Noapic"
date: 2008-02-01
forum: General Help
---

### Post by RizingDamp on 2008-02-01
Hi guys,

I know this subject has been approached many times but I have been a windows user for many years and have decided to try a platform change namely Linux.  Having read many posts I have decided upon Unbuntu as it seems to be the distro named for the beginner.  Well some time ago I downloaded Dapper Drake 6.06 LTS.  I mounted the ISO and booted from the live CD, all worked fine.  In the last few weeks I have built a new PC, Asus M2N sli Deluxe motherboard, 2gb ram, 7600GT Nvidia grapics card etc.  Now comes my problem, I popped the Live CD in and tried to boot and was presented after loading the kernel with the    APIC warning.  I did the F6 thing and typed in noapic and it booted up without problems.  Now if I go for the install to HD am I going to be presented with the nopaic error everytime I try and boot up?  Is this error likely to appear with one of the later Unbuntu distros...IE Feisty??  Also Im hoping to use 2 hard drives, XP and Linux, making linux the 2nd bootable drive after the cd/dvd drive and installing grub to the linux drive.  is this likely to work? and will I get somekind of menu upon powering up the PC like you do with a single hard drive dual boot system??

I would appreciate your advice, :)

Thanks,

Andy

---

### Post by geraldm on 2008-02-01
noapic ? 
You can add noapic to the options for the kernel you are loading.
The file to edit is /boot/grub/menu.lst  -- (backup this file before editing)
Identify the kernel that you use, add "noapic" to the options in the line beginning "kernel" 

grub can boot any hard drive.

You will get  a menu.  
It would work to install grub on the second hard drive, but you may have to go into the system bios to select the order of the bootable drives in the BIOS options.

Gerald

---

### Post by dcstar on 2008-02-02
> **RizingDamp said:**
> 
..........
 Now comes my problem, I popped the Live CD in and tried to boot and was presented after loading the kernel with the    APIC warning.  I did the F6 thing and typed in noapic and it booted up without problems.  Now if I go for the install to HD am I going to be presented with the nopaic error everytime I try and boot up?  Is this error likely to appear with one of the later Unbuntu distros...IE Feisty??  ..........

APIC messages are not necessarily problems, too many BIOSs do not conform to the APIC standards that the Linux kernel expects, sometimes they cause problems, sometimes not.

If your Ubuntu system works even without "noapic" then simply don't worry about it, you can examine the syslog file after boot up to see if there are any issues.

---

