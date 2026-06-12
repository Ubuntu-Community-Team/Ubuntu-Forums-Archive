---
title: "Updating BIOS to uefi"
date: 2013-04-20
forum: General Help
---

### Post by Wolfgange on 2013-04-20
I have a gigabyte motherboard that has EFI technology, and right now windows 7 and Ubuntu 12.10 (both 64 bit) boot fine. There is an update for my bios to enable UEFI technology. If I upgraded, would Ubuntu still bot alright and if not, what would I have to do (Even if it means reinstalling the OS). Thanks in advanced.

[CLICK HERE]("http://www.gigabyte.us/products/product-page.aspx?pid=4015&dl=1#bios") for link to specific motherboard on bios tab (top-most one is the UEFI enable one).

---

### Post by grahammechanical on 2013-04-20
I do not know but I would worry about converting an existing setup from BIOS to EFI. Think about what is necessary to install Ubuntu on a hard disk that is in a machine set in EFI mode. That is not the case at the moment. Look through this wiki page and note the section Converting Ubuntu into EFI mode

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Also think about Windows having special needs when booting on a machine in EFI mode.

Regards.

---

### Post by The Spectre on 2013-04-20
If I were you I wouldn't update to this BIOS for Three Reasons.

1) It is a Beta BIOS.

2) It doesn't add any new Bug Fixes or Features (Other than it is UEFI).

3) If you are not having any BIOS related issues there is no reason to update it.


I would wait until it is out of the Beta stage before updating it.

---

### Post by oldfred on 2013-04-20
Unless you have a real need for UEFI, I would not change either. Some with UEFI convert back to BIOS/CSM.
       Compatibility Support Module (CSM), which emulates a BIOS mode
    
Windows only boots UEFI with gpt partitioning, which means you have to totally reformat drive. Although there are some utilities that may convert from MBR to gpt.

Ubuntu will boot from gpt drives with BIOS or UEFI.

While UEFI will be the future, there are a lot of issues, most now caused by pre-installed Windows 8 with secure boot. Linux is still working on getting UEFI to work with Windows and secure boot. Ubuntu uses a Microsoft key as a workaround for now.

---

### Post by MorrisseyJ on 2013-04-29
Hi, 

I have the same question as Wolfgange.

I am looking to update my  bios, because i keep having random system freezes in 13.04 - everyone  else is lauding the stability of the release - where nothing works after  the freeze - no input, no output. The machine has even frozen during the shut-down sequence. I  had none of these problems in 12.10. 

I also have a problem where  shutting down my system results in a restart. 

These problems are sufficiently large (random freezes make my system too unstable for work) for me to think that a bios update is worthwhile. Also, my bios is very much out of date being version 1.08 with the update being to version 2.05.

I am running 64 bit on a Lenovo Thinkpad x131e, dual booting windows 7.

In the release notes for the bios update there are the following instructions:

( If this is first time to apply UEFI BIOS Version G8ET66WW/G9ET65WW (Ver.2.05) 
  or newer version, you have to do following steps. This procedure is required 
  first time only.) 
  
  Windows 7 and Windows XP: 
 
 16. Power off the computer. 
 17. Power on the computer. 
 
 18. While the "To interrupt normal startup, press Enter" message is displayed 
     at the lower-left area or lower-center area of the screen, press the F1 key. 
     The ThinkPad Setup menu will be displayed. If a password prompt appears, 
     type the correct password. 
 19. Choose "Security" then "Secure Boot" to show the menu. 
 20. Select "Restore Factory Keys" and press Enter. 
 21. Select "Yes" to restore Factory keys. 
 22. Press F10 key and select "Yes" to save and exit from Setup menu. 
 23. Then the computer is restarted. 

Like Wolfgange, can anyone tell me if updating is going to prevent me from booting to Ubuntu - which is my primary OS (ironically i only really keep windows on the machine for the bios update utility)? Also, if i update the bios, can i avoid any EFI problems by skipping some of the steps detailed in the bios release notes? If so which ones?

Any help would be very much appreciated.

Thanks,

j

---

### Post by oldfred on 2013-04-29
@MorrisseyJ
That sounds like the procedure to restore the secure boot keys for Windows 8. But if you have Windows 7 you do not need secure boot. You need to check with someone that knows the specifics of your system.
With Windows 7 are you booting with UEFI? Only a few Windows 7 have UEFI boot and none have secure boot. If booting with BIOS/CSM then any Microsoft signing keys are not required as you can only boot Windows 8 in UEFI mode with secure boot and not Windows 8 have to (but some pre-installed systems are modified to only boot Windows efi file). If you install Windows yourself you do not have to use secure boot.

---

### Post by MorrisseyJ on 2013-04-29
Thanks for the help oldfred

Ok, i'll contact Lenovo and see what they say, although i worry that they will simply tell me that they do not officially support linux. That's really why i was hoping for support on this forum. 

I am not currently booting with UEFI on windows 7, and was surprised to see this info in the BIOS update readme file. Above the instructions for Windows 7 that i posted previously, the instructions for windows 8 are: 

```
Windows 8: 
 
  1. Turn on the computer. 
  2. Restart the computer from OS menu.
```

Are you suggesting that since this is not a EUFI machine, that i do not have to worry about the update as the key won't be enabled. I had worried that the instructions below were suggesting that the update to the BIOS would add a secure boot feature to the machine. My concern then was that i would lose access to my ubuntu install.

---

### Post by oldfred on 2013-04-29
Do not really know, but if you add the key, then install Windows 8 it may then be in secure boot mode or at least will be able to be in that mode.
I would just ask Lenovo if you install Windows 8 will it have to be secure boot only? Or will it boot with secure boot off? Supposedly only pre-installed Windows 8 has secure boot.

Ubuntu will work with secure boot as grub has the Microsoft key, but some vendors modify UEFI to only boot the Windows efi file. Boot-Repair has a work around renaming files that does work for most.

---

### Post by MorrisseyJ on 2013-04-29
OK, it seems like this should be fine. I'll contact lenovo, see what they say and get back this thread.

Thanks for the input. 

j

---

### Post by markbl on 2013-04-29
My motherboard is UEFI capable but 6 months ago I chose to install 12.10 in bios mode. I always do a fresh clean install so with 13.04 I thought I would try UEFI this time. I first updated my motherboard bios to the current version, enabled UEFI, and then installed 13.04. The Ubuntu installer automatically repartioned the drive to add the EFI partition etc and it all seems to work fine. Not that I notice much difference though!

What I am suggesting is to leave the bios to uefi move to your next clean install.

---

### Post by MorrisseyJ on 2013-10-17
After recurrent problems with my wireless, i just went ahead and did the BIOS update. Everything went fine and machine is working well, althought the wireless problem was not fixed. 

To fix that i eventually had to replace my Broadcom card with a whitelisted Intel Centrino card. Now everything is working fine. 

j

---

