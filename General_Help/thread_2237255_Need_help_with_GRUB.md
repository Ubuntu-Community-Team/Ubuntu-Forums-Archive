---
title: "Need help with GRUB"
date: 2014-07-31
forum: General Help
---

### Post by Zander21510 on 2014-07-31
First: do NOT tell me to "boot from live usb" or "change bios settings". I cannot access my bios, I cannot boot from any other device. I am stuck with this damn thing because my laptop is neutered to a retarded level. I've been doing this for years and I can't get it to work short of popping the thing open and putting the SSD in another computer and I'm out of patience for simplistic solutions at this point.

Now...this started when I deleted the partition with Ubuntu on it. I didn't touch the Windows partitions. I'm stuck with the "Minimal BASH-like line editing" safe-mode GRUB prompt. I tried following the directions here ([http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)) but it doesn't work because secure boot is enabled. I've messed around with ls...for some reason I can't access my Windows drives except for the /efi drive with ls but I can access thumb drives. Windows and Ubuntu were installed in EFI mode.

My question: is there a way to boot/reboot into the system setup (like on the properly configured GRUB menu or windows 8 F8 menu) from this command line, or a way to load the Windows boot loader from this command line. I will highly appreciate any help, thank you.

---

### Post by oldfred on 2014-07-31
With secure boot on, I am not sure you can do manual boot. Only signed files are allowed.

But some systems UEFI/BIOS seem to get locked up with too many reboots. You can try a full power down cold reboot and then see if you can get into UEFI menus or boot menu.
If  a laptop also remove battery, unplug and hold power switch on for  a few seconds to drain residual power. Wait a bit to be sure then try rebooting.

Last resort is as you mention remove drive and reconfigure on a working system.

What brand & model computer? Some early UEFI systems had a major bug in UEFI design which bricked system. Originally they of course blamed Linux, but Linux developers proved you could also brick system with Windows. But most of those systems work in BIOS mode and now are 2 or 3 years old.

---

