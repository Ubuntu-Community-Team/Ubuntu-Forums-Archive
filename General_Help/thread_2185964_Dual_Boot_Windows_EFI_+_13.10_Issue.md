---
title: "Dual Boot Windows EFI + 13.10 Issue"
date: 2013-11-05
forum: General Help
---

### Post by jason-tomlins on 2013-11-05
My desktop has both Windows8 and a newly updated version of Ubuntu13.10 but now will not boot into Ubuntu. In order to boot into Ubuntu I normally have to hit F11 to get into the BIOS boot menu and select Ubuntu. From there I get the grub menu and select Ubuntu but after getting the purple splash screen I just get a black screen, then my monitor looses signal and all seems dead. The only way I can boot into Ubuntu is, from the grub menu, select recovery mode then select root terminal then at the prompt type 'restart' then Ubuntu will boot. Any ideas ?

Thanks.

---

### Post by oldfred on 2013-11-05
Recovery mode has nomodeset as a default setting.
So what video card/chip do you have? 
And do you then need proprietary drivers or a permanent setting in grub for your video?

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


And if you have to boot from UEFI/BIOS or one time key each time is Windows in UEFI mode and Ubuntu in BIOS/CSM mode?

---

