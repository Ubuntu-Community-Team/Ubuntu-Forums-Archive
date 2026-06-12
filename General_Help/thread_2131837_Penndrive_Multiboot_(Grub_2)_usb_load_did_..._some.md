---
title: "Penndrive Multiboot (Grub 2) usb load did ... something to the native OS boot"
date: 2013-04-02
forum: General Help
---

### Post by KraftyMan on 2013-04-02
Hi,

This hasn't exactly been a catastrophic incident, but today I noticed a slight slow down in Ubuntu boot after doing the following:

1 - I installed Pendrives utility for creating a multi-boot usb stick (toying around for no reason which is how all bad things start)
2 - I downloaded 2 isos for Ubuntu 12.04, 1 64-bit and 1 32-bit
3 - I used Pendrives utility to install the two isos on the usb stick
4 - I rebooted, and prompted the BIOS to boot from the usb stick
5 - Oddly, the usb stick immediately started booting but I booted to my normal grub menu (which includes memtest, win7, osx etc) instead of the grub installed on the usb stick.  I went ahead and loaded the top most linux to see what would happen and predictably my HD Linux booted as opposed to the live version.

What was odd started at this point.  The boot was suddenly much slower and I had barely had a chance to see an HDPARM error related to the USB HDD I had plugged into a USB port at the time.  This was odd as I did not notice this happening before if I had the HDD plugged in during boot (the live USB I'm running from right now is not doing it on boot up either).  After looking through some logs it seems like this same error is also what's causing my "slow boot" as the boot hangs up and waits for a few second time period immediately following this error, then repeats the error again and continues at normal speeds from there.  I'm pretty new to Ubuntu so I'm not sure exactly what might have gotten changed in my filesystem, but I assume something must have.  

I've noticed no other performance issues, the actual USB HDD still loads successfully as a SCSI and is completely accessible with no corruptions.  All other system tests check out well.   I did uninstall and delete pendrive's software, install script and iso's for the time being and doing so has somewhat predictably not fixed the problem.  I'm not sure whether it was the script, the software, or if something very strange happened during that little boot I did.

Any thoughts on what I might be able to do to address this or what may have caused this?  I've found on some forums that this is a "warning message that can be ignored" but with an 8+ seconds increase in boot time, knowing I don't -have- to experience it (I didn't before!), I'd really like to be able to fix it.  That said, any advice by any of the experienced users on how to bail myself out of this misery of my own creation, will be greatly appreciated!

Thanks!

---

### Post by oldfred on 2013-04-03
I create my own multi-boot flash drives with grub2 's loopmount, but use ext4 without journal. But I also notice some slowdown in booting as I see light flash on USB flash drive and during other activity I see it being accessed as long as I have it mounted.
Does Pendrive use NTFS as that can be even slower?

---

