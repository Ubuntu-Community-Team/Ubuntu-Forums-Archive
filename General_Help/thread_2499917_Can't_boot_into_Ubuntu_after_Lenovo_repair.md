---
title: "Can't boot into Ubuntu after Lenovo repair"
date: 2024-08-15
forum: General Help
---

### Post by vonHumboldtFleischer on 2024-08-15
Hello,

I have a ThinkPad laptop which is/was dual boot configured with Ubuntu and Windows, with a Grub screen allowing me to choose the OS at startup.
I shipped it back to Lenovo to repair broken USB ports. Despite me telling them to not touch the installation, the laptop will only boot into Windows now. &#129324;
The Ubuntu installation still exists, but it is not reachable; no option to boot it even from the UEFI menu.
I ran [diagnostics]("https://paste.ubuntu.com/p/v2dkSFVCrY/") with BootRepair and asked it to [make repairs]("https://paste.ubuntu.com/p/PGfrhjnspb/"), but they seem to have failed, with errors that mean little to me. See the logs under the links.
Thanks in advance for advice. This should be easy, but I don't have the required expertise.

MK

---

### Post by currentshaft on 2024-08-15
Cy

---

### Post by vonHumboldtFleischer on 2024-08-15
> **currentshaft said:**
> Does the BIOS have an option to disable secure boot, or use Legacy/CSM boot mode?

Secure boot is disabled but there is no option use legacy BIOS.

---

### Post by tea for one on 2024-08-15
Access your UEFI settings
Disable any/all of the following (if present)

Fast Boot
Secure Boot
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock

---

### Post by vonHumboldtFleischer on 2024-08-15
I went through UEFI settings and disabled all of those and others that looked similar, but it did not help.

---

### Post by tea for one on 2024-08-15
Line 285 - 1:1049kB:274MB:273MB:fat32:EFI system partition:boot, [COLOR="#0000FF"]hidden[/COLOR], esp, [COLOR="#0000FF"]no_automount[/COLOR];

Boot into a "Try Ubuntu" live session.
Open gparted
Select your ESP nvme0n1p1
Remove the [COLOR="#0000FF"]hidden[/COLOR] flag and the [COLOR="#0000FF"]no_automount[/COLOR] flag

May help, may not - just a guess at the moment

---

### Post by vonHumboldtFleischer on 2024-08-15
Didn't work but thank you for trying.

How bad would it be to reinstall GRUB to the EFI partition, as explained for example in [this article]("https://gcore.com/learning/how-to-install-grub-bootloader-in-linux/")?

Also, I am confused by a few things in these logs. What even is /dev/sda and why is it bootable? This computer has a single 4TB drive as far as I know. And why the mismatch of sector numbers for the 4th partition of /dev/nvme0n1? By looking at the disk info under Windows, this is likely a "Windows Recovery" partitition, which may or may not have existed before the update. Could Lenovo have added it during repairs and confused things?

---

### Post by tea for one on 2024-08-15
The article is for Legacy Grub, you have Windows and Ubuntu in UEFI mode.
/dev/sda in the boot-repair output is your live usb (Kingston DataTraveler)

Here is a link for instructions to re-install Grub via a live session to a UEFI installation.
You have to be careful and choose the correct disk nomenclature for your PC - please do not blindly follow the guide.
i.e. you have an nvme internal disk 
[https://techbit.ca/2018/09/repair-grub2-efi-boot/](https://techbit.ca/2018/09/repair-grub2-efi-boot/)

---

### Post by dragonfly41 on 2024-08-15
In Windows there is an app EasyUEFI (search for it) and you have some time in free trial to inspect from Windows side. Whether you retain it is up to you but you should gain some insights during trial term. Other than that I would install rEFInd and in BIOS (F2 or F10 or whatever when starting up) select that as your primary boot option. It does not replace Grub. They sit side by side as boot options in BIOS. I always use rEFInd.

---

### Post by vonHumboldtFleischer on 2024-08-15
Thank you all for helping.

I tried reinstalling Grub using the tutorial. In the process I got:

```
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
```

This message was also in the Boot-Repair logs. I completed the process but nothing changed. The computer boots into Windows and there are no additional boot options available.

I'm not sure what to do with EasyUEFI, but it showed me that the contents of the EFI partition is
```
- $RECYCLE.BIN
  desktop.ini
- BOOT
  BOOT.SDI
- EFI
  - Boot
  - Microsoft
  - ubuntu
- System Volume Information
  IndexerVolumeGuid
  WPSettings.dat
```

which looks like Windowsy crap potentially interfering with a normal setup? The tutorial only had the EFI subdirectory here. Should I boot back with a live USB and delete everything except EFI?

I migt try rEFind next but curious if any of this information helps with diagnosis.

---

### Post by tea for one on 2024-08-15
> **dragonfly41 said:**
> Other than that I would install rEFInd and in BIOS (F2 or F10 or whatever when starting up) select that as your primary boot option. It does not replace Grub. They sit side by side as boot options in BIOS. I always use rEFInd.
Yes, rEFInd is a good recommendation, especially that it can be used as bootable usb (without installing)
Also, rEFInd offers an option to boot the Ubuntu kernel directly, in effect, bypassing Grub.
Certainly worth trying.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File

---

### Post by werewulf75 on 2024-08-15
> **vonHumboldtFleischer said:**
> Hello,  I have a ThinkPad laptop which is/was dual boot configured with Ubuntu and Windows, with a Grub screen allowing me to choose the OS at startup. I shipped it back to Lenovo to repair broken USB ports. Despite me telling them to not touch the installation, the laptop will only boot into Windows now. &#129324; I know it's no help here, but just for the future. *Always* remove all and any disks from any device that you submit for repair or whatever, and always lock your UEFI/BIOS settings with a strong password or, if available, biometrics. Not sure if all Thinkpads support biometric, both of mine certainly do. (Although, I never use that, preferring strong passwords.)

---

### Post by vonHumboldtFleischer on 2024-08-15
Thanks to rEFInd I managed to boot into my Linux and reinstall grub from there.
This completed without error and grub menu shows at startup now.
Many thanks again to everyone.

---

### Post by #&amp;thj^% on 2024-08-15
It's hard to go wrong with rEFInd, :)

Grub is a boot loader, rEFInd is a Boot Manager, and they live together nicely.
Good Job...

---

### Post by oldfred on 2024-08-16
I think there is a bug some where with grub or modprobe.
grub-install: info: executing modprobe -q efivars.
If you have UEFI boot entry, you can ignore error.
Seems to be from systems upgraded, vs. new installs.

Error seen as missing efivars in kernel folder in /boot.
But efivars really here:
ls /sys/firmware/efi/vars
My fstab shows this:
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)

If you need efivars mounted add to either Boot-Repair or chroot commands to mount it to correct location.
chroot needs this in addition to other commands:
mount -t efivarfs efivarfs /sys/firmware/efi/efivars

---

