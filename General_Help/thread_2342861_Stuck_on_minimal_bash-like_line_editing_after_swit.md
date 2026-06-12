---
title: "Stuck on minimal bash-like line editing after switching back to windows"
date: 2016-11-10
forum: General Help
---

### Post by lapplebaum on 2016-11-10
Hi, I have had Ubuntu Gnome installed on my Toshiba P50t for a few months now, and have recently decided to switch back to Windows 8.1 for software compatibility reasons. I successfully reinstalled windows on the disk partition that previously had Gnome. While I was downloading and setting up many of my Windows programs, I restarted my computer several times, and had no issues. However, once I put the computer to sleep, and turned it back on, I was presented with a black screen that reads as follows:


GNU GRUB version 2.02~beta2-29ubuntu0.3

Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device or file completions.

grub> _


My knowledge of BASH is limited, and I cannot seem to access anything else including the UEFI boot menu and usb drive, and not even the Toshiba splash screen shows anymore. I tried the ls command and get:

(hd0) (hd1) (hd1,gpt6) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1)
error: failure reading sector 0xfc from 'hd0'.
error: failure reading sector 0xe0 from 'hd0'.
error: failure reading sector 0x0 from 'hd0'.
 
I tried to boot each one of them, but I get:

error: you need to load the kernel first.

Thank you in advance for any help. I have no idea what to do.

---

### Post by yancek on 2016-11-10
You still have Grub boot code somewhere which should not be the case if you installed windows correctly.  Possible problems might be a mix of EFI/MBR.  Best thing to do is to google "boot repair Ubuntu" and go to the site and download the script, burn it to a CD and run it and select the Create BootInfo Summary option.  You can post a link to the output here and it should give those members familiar with EFI enough info to make a suggestion.

---

### Post by lapplebaum on 2016-11-10
Thanks for the quick response! I tried to install the ubuntu repair tool a usb drive and run it from there, but it boots directly to the [COLOR=#000000]Minimal BASH-like line editing interface, and I cannot seem to access the usb drive. Is there a reason it may work from a cd rather than a usb drive? Even if before this problem, my UEFI boot priorities went usb, then HDD, then CD? If so, it's worth a shot. Also, I have since been able to remove my HDD and access my windows files from another pc using a hard drive enclosure. However, I can ONLY see the windows files, no trace of grub or ubuntu. Do you think I may be able to get rid of grub if I access the drive via another ubuntu machine? Or a special windows tool? Thank you once again![/COLOR]

Okay, since my second post, I have installed a program called Ext2Fsd on my other PC, which is supposed to be able to recognize Ubuntu file systems. My drive from the computer stuck on GRUB if local disk F. I see several partitions. Most are NTFS, which I believe are Windows The largest partition of 920 GB is able to be read by my PC as a removable drive. I have attached a screenshot of the program. Does anybody know which drive(s) would be the residual broken pieces of Ubuntu/GRUB? I do not want to delete anything important, and I also have noticed that while to C: drive has a EFI system partition, while my F: drive does not. Might this be the reason that I also don't even get the Toshiba splash screen anymore or UEFI settings anymore? Thanks again!

[ATTACH=CONFIG]272064[/ATTACH]

I will keep updating this thread on my progress. I have been able to boot into my windows partition on my hard drive by configuring my other PC's bios settings to boot from the drive via usb. I have also been able to access the minimal bash-like line editing in the same way. My problem of not being able to access Windows while hard drive is installed still persist though.

---

### Post by dankegel on 2016-11-11
Googling "uninstall grub" finds some interesting bits, for instance

[https://www.techmesto.com/uninstall-linux-grub-dual-boot-windows8/](https://www.techmesto.com/uninstall-linux-grub-dual-boot-windows8/)

Do any of those help?

---

### Post by lapplebaum on 2016-11-11
Thanks for the response. Those are all well and good, but the problem is I can't actually change the boot order on the drive. Like I said, I get no Toshiba splash screen which is normally when I would hold F2 to access the EFI boot menu. I'm unable to boot into anything other than the minimal bash like line editing. No other partitions, and no USB drives. I am only able to access my windows partition only by plugging the drive into an enclosure, and changing the EFI / bios settings on a different PC to choose to boot the windows partition over USB.

---

