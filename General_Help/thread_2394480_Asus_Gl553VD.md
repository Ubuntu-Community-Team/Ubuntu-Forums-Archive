---
title: "Asus Gl553VD"
date: 2018-06-16
forum: General Help
---

### Post by waloshin on 2018-06-16
I7 7700HQ
Nvidia gtx 1050 4gb, intel hd630 intel optimus

Ububtu 18.04 freezes on install and try. 


Watchdog: Bug soft lockup - cpu#3 stuck for 22s! [Modprobe:1179]

Keeps switching between 3 and 6.

---

### Post by oldfred on 2018-06-17
Are you using nomodeset? Many Asus also need pci=nomsi boot parameter.
And all systems need UEFI update? Have you updated UEFI from Asus?

Similar model, older install, but may need same fixes.
       Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

General UEFI install:
       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
See also link below in my signature.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

Some have turned off nVidia in UEFI and installed using Intel video. Then added nVidia driver from Ubuntu repository or ppa and enabled nVidia.

---

### Post by waloshin on 2018-06-17
Thank you for the reply I do have the latest uefi from Asus. I did get it running using NOMODESET. Thank you.

---

### Post by oldfred on 2018-06-17
Glad it worked, you can change thread  to solved.

---

