---
title: "GRUB2 installation query"
date: 2013-05-15
forum: General Help
---

### Post by SpeedoJoe on 2013-05-15
I am currently writing a script for work which commissions two partitions (the first is a recovery envrionment, the second being the main OS with propitiatory software installed) and I have come to the final process, GRUB2 installation.

I basically have it working but the tutorials I have found specify that I should mount /dev, /proc and /sys before running grub-install. I have tried it without and the boot menu is seemingly restored correctly.

I'd like to understand this process further. Would someone please explain why the three mount points above are required?

Thanks.

---

### Post by grahammechanical on 2013-05-15
The best help that I can give is to direct you to the official Grub manual.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Regards.

---

### Post by oldfred on 2013-05-15
There is the quick two line reinstall of grub2's boot loader to the MBR and the full chroot. 
I think the quick works if the liveCD you use is the same version, any version a lot different or a full reinstall of grub2 not just grub to MBR requires the full chroot.

        RestoreUbuntu/XP/Vista/7Bootloader & Windows 8 (not UEFI)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

   Gui, Terminal & alternate install CD rescue grub repair
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

