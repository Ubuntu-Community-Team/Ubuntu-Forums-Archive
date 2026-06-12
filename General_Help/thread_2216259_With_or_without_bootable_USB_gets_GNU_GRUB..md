---
title: "With or without bootable USB gets GNU GRUB."
date: 2014-04-10
forum: General Help
---

### Post by zmbronx on 2014-04-10
After installed Ubuntu 13.10, formally Windows 8 PC didn't boot without the bootable USB threfore changed back the boot order at UEFI 1st Boot HDD 2nd Boot USB.  Now, with or without the bootable USB,  PC only gets "grub >"

Brandnew DELL INSPIRON 2020 /4GB /1TB.
There was no file therefore all HDD space was allocated to Ubuntu (no dual boot partitions)  Before the "grub >" problem starts, I saw C: had EXT 4 and Swap had 50GB.
 
At first, Windows 8 didn't let the bootable USB to load even I disabled its secure boot.  Therefore I changed UEFI boot order as 1st USB, 2nd Disable, 3rd NIC, 4th something (DVD? but not HDD) was able to install Ubuntu.  After  the installation, with USB I was able to load Ubuntu seemed all fine.  Since I changed UEFI with no HDD boot (because windows 8 didn't let USB to install), I corrected it to 1st Boot: HDD, 2nd: USB, 3rd: NIC, 4th something (DVD? but not HDD).  Now all it gets "grub >" with or without the bootable USB. 
 
Entering "boot repair got "load the kernel first" message.
"ls" gets "failure reading sector Oxfc from 'hd1', OxeO from 'hd1', OxO from 'hd1'.
 
Any chance to recover it?

---

### Post by Double.J on 2014-04-11
Hi there!

welcome to the forums!

looks like grub can't find where the kernel is on the hdd.

the reason this happens on usb or hdd is that you have told the uefi to boot yhe hard drive first - it isn't even looking at the usb. 

If there is an option called boot select when you power on, press the corresponding key and boot from the usb, if not, go back into the uefi menu and set usb above hdd. 

Then boot from the usb and try running [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), then restart the machine. Be sure to remove the usb when asked when you restart.

best of luck!

Jj

---

### Post by zmbronx on 2014-04-11
Thank you for your reply.  I just made a donation as well.  (Yes, I love Ubuntu.  My burnt out XP machine had it for 4 ~5 years.)
 
F12 key only gets me to 'Change Boot Mode Setting' -- Legacy Boot Mode or UEFI Boot Mode.  It doesn't get me to Boot order setting.  Do you happen to have grub command leads me to Boot Order?
 
Otherwise I will read the link below over weekend, hoping I will be able to figure it out.
 
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

But the problem is that "ls" doesn't get me any drives...
 
Sincerely,

---

### Post by Double.J on 2014-04-11
Hi

unfortunately grub can't change the boot order of the bios.

just incase it's helpful, here's what happens at boot; you turn on the computer, and
1) the motherboard software (bios - older machines, uefi-new machines) loads first. It is all the text and images before grub.
2) the boot sector of the hard drive is loaded and takes charge. This is grub in your case.
3) grub hands over to the system kernel in the /boot directory
4)kernel loads init and your system begins to boot.

at the moment you're stuck at 2) - grub is installed on the hard drive. Your uefi bios hands boot over to grub and it doesn't know what to do.

at power up look for 'enter setup' or 'edit settings' it's the option you used to sett the hdd above the usb. For now all we need to do is boot from your usb, which is unaffected, not the hard drive where the broken grub is.

once booted from the usb you can follow the boot repair instructions in the link from my previosu post to try and fix grub and get your hdd to boot.

Jj

---

### Post by zmbronx on 2014-04-11
with F12 (UEFI BOOT: /UEFI: 0.00), I was able to load ubuntu with USB now, able to load Boot Repair but can't remove GRUB 2 says:
 
Errors were encountered while processing: gconf2
 
There seems lot of discussion about how to remove Grub 2.  I will read them later.  Gotta go back to work for now.

---

### Post by oldfred on 2014-04-11
If you can get into Boot-Repair.

 
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

