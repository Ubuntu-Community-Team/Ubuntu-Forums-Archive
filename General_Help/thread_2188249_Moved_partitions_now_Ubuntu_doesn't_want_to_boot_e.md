---
title: "Moved partitions now Ubuntu doesn't want to boot even though it did once afterwards"
date: 2013-11-16
forum: General Help
---

### Post by allesstill on 2013-11-16
I use Ubuntu more than I use Windows so I decided to shrink my Windows partition and add it onto my Ubuntu partition(s). I needed the space on my "/" partition but my "/" partition was not located next to the Windows partition I had just shrunk, so I moved my partitions until the unallocated space was next to the "/" partition. When I resized my Windows partition, I used Windows and to move the Ubuntu partitions I used an Ubuntu Live CD. Everything seemed to go smoothly so I shut down and booted into Ubuntu normally and it worked perfectly. There were no issues with Ubuntu and the additional space had been added. To make sure everything went okay on both ends, I shut down Ubuntu and booted into Windows. Windows worked normally, no issues or anything.

**Here's where my issue gets a little unique: **My laptop came with Windows 8 pre-installed; UEFI, secure boot, etc. When I installed Ubuntu, I manually created the partitions in Windows and installed Ubuntu onto them from a Live CD. In order to boot into Ubuntu, I have to disable UEFI and enable CSM booting from the boot settings menu (accessed by pressing F2 during my computer's loading screen) and in order to boot into Windows, I have to disable CSM and reenable UEFI booting. It's kind of awkward but it works perfectly and I don't boot in and out of them that often anyway.

However, and **here is my issue**, after I enable CSM booting, instead of being taken to the purple GRUB screen like I usually am, I get a black screen with one of those blinking _ things likes it's waiting for me to input text (although it doesn't allow me to). This just worked moments before, why won't it let me boot back in?

---

### Post by fantab on 2013-11-16
Reboot again and see if it helps.

The reason for your 'awkward problem' is that Windows is installed in UEFI mode but you Installed Ubuntu in Legacy mode, when you should have installed it in UEFI mode as well.
If Rebooting doesn't help then boot with Ubuntu Live DVD/USB and 'Try Ubuntu without installing'.

Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") and create '**BootInfo Summary**', make note of the LINK it creates and post it here.

If you want to fix your 'awkward problem' then ENABLE UEFI, boot with UBUNTU DVD/USB in UEFI mode [you should see BLACK screen with options if booted in UEFI mode] and run 'Recommend Repair' from Boot-Repair after installing it. Boot-repair will install GRUB in UEFI mode.

---

### Post by allesstill on 2013-11-16
> **fantab said:**
> Reboot again and see if it helps.

The reason for your 'awkward problem' is that Windows is installed in UEFI mode but you Installed Ubuntu in Legacy mode, when you should have installed it in UEFI mode as well.
If Rebooting doesn't help then boot with Ubuntu Live DVD/USB and 'Try Ubuntu without installing'.

Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") and create '**BootInfo Summary**', make note of the LINK it creates and post it here.

If you want to fix your 'awkward problem' then ENABLE UEFI, boot with UBUNTU DVD/USB in UEFI mode [you should see BLACK screen with options if booted in UEFI mode] and run 'Recommend Repair' from Boot-Repair after installing it. Boot-repair will install GRUB in UEFI mode.
When I run the Live CD with UEFI enabled, after I select  "Try Ubuntu without installing" I get a black screen and I can hear that the disc has stopped spinning. Any idea?

---

### Post by oldfred on 2013-11-16
What video? 
If nvidia you need nomodeset and if Intel you probably need Intel specific settings.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 Some other Intel boot options - varies by vendor & Intel chip version.
acpi_osi=Linux  acpi_backlight=vendor

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

---

