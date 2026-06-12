---
title: "Problem with booting kubuntu x64, EFI"
date: 2013-01-06
forum: General Help
---

### Post by lavruh on 2013-01-06
Hello, I had normally run kubuntu 12.04.1 (x64) on my sony vaio laptop  before, few days ago, installed updates for EFI. Next boot I got GRUB  menu but when try to start kubuntu I saw on the screen  *error: symbol not  found: `grub_efi_secure_boot'.* On recovery mode same.
I  tried boot-repair it did not help, then tried to install 12.10 bad  results - no menu at all, than I downloaded 12.04.1 and installed it  again and now have menu but the same error when try to start kubuntu. 
Here is my last boot-repair report [http://paste.ubuntu.com/1503274/](http://paste.ubuntu.com/1503274/)

Can somebody help me.
Regards.

---

### Post by Rsjc741 on 2013-01-06
Looking at the pastbin, it looks like you're using the windows installer to dualboot Kubuntu.

So if you're using Wubi to install a bootloader, please try the traditional method instead.

If that method fails, you might have to format + 0 out your hard drive.

---

### Post by oldfred on 2013-01-06
If you have Windows 7, you should not have secure boot. If system came with Windows 8 then the UEFI would have secure boot and you need to install 12.10 64 bit version to have the secure boot capability. 

But you need to turn secure boot off and turn fast boot off in UEFI/BIOS.

But your Windows seems a bit confused. You seem to have BIOS boot files & efi Windows boot files in the Windows partition and two FAT32 partitions. Only one can be efi but you seem to have efi boot files in both. Some systems do seem to have extra boot files in another partition which seems to be only used to get to recovery partition.

Some others with Sony's that worked.

       Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

            Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
[       ]("http://ubuntuforums.org/showthread.php?t=2090605")
 Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

---

### Post by lavruh on 2013-01-08
The solution is found. The problem was that I forgot nuances of last installation.
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works :D
 
Thanks everybody for support))

---

