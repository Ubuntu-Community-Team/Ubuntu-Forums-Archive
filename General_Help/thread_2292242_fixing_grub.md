---
title: "fixing grub"
date: 2015-08-26
forum: General Help
---

### Post by jim50 on 2015-08-26
Hi all, So my installation of grub during install failed. I booted the live usb stick again and am trying to use boot-repair without a lot of luck.

I have two hard drives, one for OS and one for data, both formatted GPT. I have windows 10 installed in UEFI mode, but having long learned what a chore UEFI is, I was previously multibooting by turning legacy mode on and off - on, ubuntu/other OS boot, off windows boots in secure mode. It seems that boot-repair is seeing that EFI partition that windows creates and deciding I want a UEFI install, when infact I just want to use GPT disks in legacy mode.

Any advice?

Thanks,

Jim

---

### Post by sheriff-pointing on 2015-08-26
Have you considered an EFI bootloader such as refind or clover, and then installing grub on the partition (rather than the disk)?

---

### Post by jim50 on 2015-08-26
Wouldn't that require booting in UEFI mode?

---

### Post by sheriff-pointing on 2015-08-26
Yep, it does, but I have found that EFI booting works well with almost anything except GRUB.  Refind or clover will give you a graphical menu on bootup, and can either boot directly into linux, or chainload grub.  

I'm actually not sure why they stick with grub.  Refind configures itself.  I've never had to touch a config file.

Although, I have only used them to dual boot Ubuntu and OSX, but they should also work on Windows 8. (Whoops, dunno about Win 10 though, sorry for not reading properly.)

---

### Post by jim50 on 2015-08-26
hmm... I shall try a chroot manual grub install and see where we're at first, but I may have to come back to UEFI boot *shudders*

EFI Just annoys me on this laptop because it somehow boots slower than the old system dispite supposedly already knowing where it needs to go 0.o

Not a fan of Acer for this firmware.. my asus desktop's efi is so nice... *le sigh*

---

### Post by sheriff-pointing on 2015-08-26
Sorry to hear that.  I have to agree with you though, EFI still is a bit of a pain.

If you decide to go down the EFI path though, take a look at this page:[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html) 
You can download an image to put Refind on a flash drive, and use it to boot your installed OS.  It may save you a bit of time, and allows you to try refind without installing.

---

### Post by oldfred on 2015-08-26
Many with UEFI issues have used rEFInd. I have not tried it yet.

If you have an Acer and in UEFI mode must enable "trust" for Ubuntu/grub's efi boot files. You have to set supervisory password.
       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

Better to have both systems in UEFI boot mode. 
But you can have Ubuntu in BIOS boot mode if you add the 1 or 2MB unformatted partition with the bios_grub flag on each drive you install grub to gpt's protective MBR. You then can only boot from UEFI, may have to turn on/off UEFI or BIOS mode to change how you boot. Some do remember and let you use a one time boot key like f10 or f12. UEFI and BIOS are not compatible and once you start booting in one mode you cannot switch. Or you cannot use grub to dual boot unless both systems are in same boot mode.

---

### Post by jim50 on 2015-08-26
Thanks for the help guys, still dont know why the boot-repair couldnt do it, but purging and reinstalling grub2 from a chroot and forcing it onto the bios_grub apce worked. 

Just FYI, EFI install and boot does work fine on this laptop out of the box, sorry for the confusion. I just choose not to use it for three reasons:
 1) it's slower to boot, like adding 10 seconds to a 20 second boot.

 2) I discovered a horrible risk factor with this firmware that has never happened before; my 14.04 did a kernel update back around jan/feb time and something went wrong. I assume it was in updating the EFI partition, but I'll never know. Essentially what happened was it bricked the board - you couldnt enter the firmware, just see the ACER page come up at boot, disapear and fall into a code-hole. No beeps, no keyboard input, just a black screen and a power light. I had to use a reset button on the bottom of the laptop as even holding the power button down couldnt turn it off. The fix was to take the battery out for a couple of minutes, to reset the firmware, Then boot the windows installer, which couldnt repair the boot and reinstalled itself, then repair grubefi. 

3) I have to go back into the firmware either to turn secureboot on/off or boot select anyway. 

So for me the best system is to have windows as the only EFI booting OS so it gets it's secure boot partition, and my ubuntu / #!++ booting in tradtitional legacy mode so they boot faster and there's no risk of EFI meltdown lol!

---

