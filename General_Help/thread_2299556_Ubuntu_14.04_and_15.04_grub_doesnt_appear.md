---
title: "Ubuntu 14.04 and 15.04 grub doesnt appear"
date: 2015-10-19
forum: General Help
---

### Post by KkaotikK on 2015-10-19
[COLOR=#000000]hello, i have a packard bell imedia l4875 with updated w10, so i partitioned the disk 4 ubuntu and installed, when the installation finishes and pc restart take me directly to windows... i reinstalled 3 or 4 times windows and ubuntu 7 or 8... i tryed boot repair and everything i can googled, i think the problem is in the hardware or something... if anyone can help please reply me thank you!!![/COLOR]

---

### Post by yancek on 2015-10-19
Did you install Ubuntu using UEFI?  Windows 10 uses GPT and UEFI by default so if you don't install Ubuntu in UEFI, it won't boot.  You forgot to post the boot info summary from boot repair which would be very useful for someone to help you.

---

### Post by KkaotikK on 2015-10-19
[http://paste.ubuntu.com/12862536/](http://paste.ubuntu.com/12862536/)

---

### Post by KkaotikK on 2015-10-19
i try to delete the free space i reserved for ubuntu and reinstall and tell me if i want to install ubuntu with windows boot manager and i cliked yes but not work

---

### Post by oldfred on 2015-10-19
From UEFI or one time boot key, often f10 or f12 can you boot the ubuntu entry?

Not seen many Packard Bell systems, but many systems need work arounds as vendor modified UEFI to only boot by description and only valid description is "Windows".  That is not per UEFI standard.

Most use the copy & rename of shimx64.efi to /EFI/Boot/bootx64.efi
Also details in link below in my signature.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
            
Packard Bell Easynote manually renamed bootx64.efi, but best not to rename Windows efi boot file. Windows will overwrite that with updates anyway.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by KkaotikK on 2015-10-19
with f12 i can choose from i want to boot, only appears 500 gb hdd and takes me directly to windows...

---

### Post by oldfred on 2015-10-19
Then copy /EFI/ubuntu to /EFI/boot and rename shimx64.efi to bootx64.efi.
You may have to also use efibootmgr to add the hard drive boot entry to UEFI boot menu.

---

### Post by KkaotikK on 2015-10-19
well... i installed from 0 w10 and ubuntu 15.04 with default install settings... nothing happened... grub not appears... any tips???

i have secure boot disabled etc...

---

### Post by yancek on 2015-10-19
Did you copy and rename the files suggested above by oldfred?

---

### Post by KkaotikK on 2015-10-19
[http://paste2.org/yDw6z1CA](http://paste2.org/yDw6z1CA)

---

### Post by oldfred on 2015-10-19
Report does not show if files were copied or not as per post #5.

---

