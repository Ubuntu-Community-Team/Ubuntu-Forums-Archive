---
title: "Dual boot jumps to Windows without showing grub/ubuntu"
date: 2021-07-17
forum: General Help
---

### Post by m-atek on 2021-07-17
Hi, 


I have Windows 10 and Ubuntu 20.04 installed on a single drive in my Dell G5 5587 with Intel 8th generation CPU. I installed Ubuntu from a bootable pendrive just fine, and now even if I have Ubuntu as the top option to in boot options, it still runs Windows directly on laptop start. I have also run bcdedit command in cmd, nothing changed. When I choose to boot from "ubuntu", I get an error message in BIOS saying "no bootable device found" and the only option is to shutdown. :(

 

Let me know if you need more information. 


Please let me know how to proceed.  

 
Kind regards.

EDIT: I fixed it by manually adding one more entry to boot menu in BIOS, re-installing ubuntu and using a file EFI\ubuntu\shimx64.efi

---

### Post by yancek on 2021-07-18
>  EDIT: I fixed it by manually adding one more entry to boot menu in BIOS,  re-installing ubuntu and using a file EFI\ubuntu\shimx64.efi 		

Did you have Secure Boot enabled during the first install?  Generally, the problem in a dual boot you described is installing in different boot modes, UEFI an Legacy/CSM though that does not appear to be the case here.  The links below should be helpful in the future, the first the official Ubuntu documentation for dual booting with windows 10 and the second the boot repair software which is really helpful with boot problems on Linux and can provide a lot of useful information when you need help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Good job getting it working.

---

