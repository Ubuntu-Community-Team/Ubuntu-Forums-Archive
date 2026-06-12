---
title: "&quot;Firmware Bugs&quot; -- recent 22.04 install-- options to flashing BIOS?"
date: 2024-02-20
forum: General Help
---

### Post by ishmael3 on 2024-02-20
Have been getting these boot warnings since installing 22.04. Not blaming on 22.04,  probably something I did, but I don't know what.  System worked fine with 20.04.
 
 ```
tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
```
 
 ```
x86/cpu: SGX disabled by BIOS
```
 
 ```
DMAR: [Firmware Bug]: No firmware reserved region can cover this RMRR [0x000000008d800000-0x000000008fffffff], contact BIOS vendor for fixes
```
 
 
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=293423&stc=1[/IMG]

I experience only two issues: 1) System occasionally doesn't wake from sleep -- *actually*, doesn't* properly* *suspend* in the first place (fan continues to run even while system is non-responsive). 2) Then CPU power button behaves differently -- holding button down first stops the fan (power button stays lit, system still suspended) -- then *second* push reboots.  

 Sleep/wake works properly 95% of time. In normal use, system functions fine. Always boots and shuts down smoothly. But, obviously, something is wrong and needs addressed.  
 
 One approach might be to update firmware but this seems unlikely as a solution to me. One reason is that installed firmware worked fine with 20.04. Second reason is that available firmware updates make no mention of addressing any power/suspend issues.  
 
 Opinions would be appreciated. Would it make sense to risk bricking machine with a BIOS/Firmware update? Or is there (I hope) some better way to approach this?
 
 Computer is a seven-year-old Aspire TC-780, Intel Core i5 processor 6400, Intel HD Graphics 530. Straight forward install of 22.04 -- no dual-boot, no unusual downloads. I can't find any "SGX" in BIOS settings. 
 
 Thanks for any suggestions.

---

### Post by ishmael3 on 2024-02-20
I tried to add an image of the boot screen in first post but only see  the image if logged in to forum -- I hope that's the way it's supposed  to work.:P

---

