---
title: "computer still boots into W10 even with lubuntu as the first boot drive."
date: 2018-10-05
forum: General Help
---

### Post by yuioni on 2018-10-05
so i'm not sure what the deal is, but after installing lubuntu on one of my drives in my system. i tried to boot directly from that drive (via f12 to make sure windows didn't get a chance) but windows still boots instead. i looked at the drive and windows can't "see" the drive anymore as far as how much space it has. (shows 0 bytes) so i know something is there. i installed lubuntu under ext 4 if that makes a difference.

my drive set up is this:
480GB SSD <-- windows 10
1TB 7200rpm <-- lubuntu
3TB 5200 RPM <-- data drive

i specifically made sure that the dvd drive and the 1TB had first boot priority and disabled a 3rd boot option and still windows finds it's way to the screen. i googled around for a quick minute and didn't find anything of this particular issue, so i thought i would seek out external help. i'm looking to dive head first into linux as i've been in the windows world for the last 20 years. time to learn some new tricks. thanks for any help with this!

edit. lubuntu version is lubuntu-18.04-desktop-amd64

---

### Post by oldfred on 2018-10-05
Are these internal drives or USB external drives?

Make sure any external drives are plugged in.
       Just run the summary report, the auto fix sometimes can create more issues. Use ppa version in your live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yuioni on 2018-10-05
> **oldfred said:**
> Are these internal drives or USB external drives?

Make sure any external drives are plugged in.
       Just run the summary report, the auto fix sometimes can create more issues. Use ppa version in your live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



Thank you for your reply!

so i downloaded the file you referenced. i made a live USB with universal USB installer. i went to bios and made it first boot priority, saved and exited, pushed f12 for boot menu and picked the drive directly and the system booted directly into windows 10. did not pass go and gave me no option to collect 200 bucks.. i did change the bios from a windows 8/10 boot set up to "other OS" thinking that may have been the issue. no help with that tweak though. i was able to get linux mint on a secondary computer with out much trouble the other day but it only has 1 drive, however it is dual booted. apparently windows 7 is a lot more lenient of sharing it's hard drives than big ol windows 10.

---

### Post by oldfred on 2018-10-05
What brand/model system? What video card/chip?

Most Windows 7 systems were BIOS/MBR. Since Windows 8 systems are UEFI/gpt.

Usually best to have "Other" rather than "Windows" as that really is UEFI Secure Boot setting. Some systems mention that if installing Windows 7 in either BIOS/CSM/Legacy or UEFI you must use "Other" as Windows 7 does not support UEFI Secure Boot.

If UEFI Secure boot is on, you almost always have to also change USB settings to allow USB boot. Allowing another system to boot is considered insecure. 
But even if Secure Boot is off, you may need to change USB settings to allow boot.

But some have had issues with flash drive, and different one then worked. Some have had issues with USB port & different one worked. And some just needed to download Ubuntu again & verify md5sum to be sure download is correct.
Also some ways of making USB flash drive work, or work better than others for unknown reasons.

       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
       UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
            Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by yuioni on 2018-10-05
> **oldfred said:**
> What brand/model system? What video card/chip?

Most Windows 7 systems were BIOS/MBR. Since Windows 8 systems are UEFI/gpt.

Usually best to have "Other" rather than "Windows" as that really is UEFI Secure Boot setting. Some systems mention that if installing Windows 7 in either BIOS/CSM/Legacy or UEFI you must use "Other" as Windows 7 does not support UEFI Secure Boot.

If UEFI Secure boot is on, you almost always have to also change USB settings to allow USB boot. Allowing another system to boot is considered insecure. 
But even if Secure Boot is off, you may need to change USB settings to allow boot.

But some have had issues with flash drive, and different one then worked. Some have had issues with USB port & different one worked. And some just needed to download Ubuntu again & verify md5sum to be sure download is correct.
Also some ways of making USB flash drive work, or work better than others for unknown reasons.

       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
       UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
            Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)



thank you fred for seeking this out with me. the solution has been found but i will share everything that i did to hopefully help others.

i installed lubuntu on my 1TB hard drive but windows kept taking over.
so i had to disable the SSD drive with windows 10. turn off fast booting in bios.
i reinstalled lubuntu directly to the 1TB again. this time it found the old install so i over wrote that old install.
i pulled the flash drive and restarted to make sure lubuntu worked.
the OS worked fine then. next i re-enabled the SSD with windows on it and booted up. lubuntu took priority boot at that point.
so the next step was to update the grub command. grub found the other OS and i was able to use both OS's from that point on, with the 1TB drive with lubuntu as the primary boot drive.

thank you again fred.

(i also did change my boot setting from windows 8/10 changed to "Other OS" but i'm not sure that helped anything because i did that before i even asked for help)
i do not load OS's from disks anymore. i've used flash drives only for installing OS's for about 10 years now.

i'm also on a custom built system GA-H270N-WIFI with a i3 7350k, 16GB DDR4, and a GTX 1050TI.

---

