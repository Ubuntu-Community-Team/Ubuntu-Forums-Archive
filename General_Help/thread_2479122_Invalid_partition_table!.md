---
title: "Invalid partition table!"
date: 2022-09-15
forum: General Help
---

### Post by adventure man on 2022-09-15
Hey guys, I get this at startup of my Dell Latitude E6430. If I hit enter or space bar the computer continues to load, if not, it will just sit there with this message.

I installed xubuntu 22.04 with a USB stick. Windows 10 was on it previously.

Any help is appreciated. Thank you :guitar:

---

### Post by ne29914 on 2022-09-15
Did you partition and format (ext4) the disk during installation?

---

### Post by adventure man on 2022-09-15
> **ne29914 said:**
> Did you partition and format (ext4) the disk during installation?

I did a complete format, kept nothing from WIndows and just did the sole install of Xubuntu.

---

### Post by &amp;KyT$0P# on 2022-09-15
What happens if you change the [FONT=Courier New]GRUB_TIMEOUT_STYLE[/FONT] line in [FONT=Courier New]/etc/default/grub[/FONT] to
```
GRUB_TIMEOUT_STYLE=menu
```
and then run [FONT=Courier New]sudo update-grub[/FONT] to apply this change?

---

### Post by oldfred on 2022-09-15
Please do not post screen shots of terminal output. Just copy & paste terminal output in code tags.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)


You show both bios_grub for BIOS boot and ESP - efi system partition for UEFI boot?
New systems are UEFI with gpt partitioning. So did you install in old BIOS boot mode?
How you boot install media UEFI or BIOS is then how it installs.

What does this show?
sudo gdisk -l /dev/sda

Query to check if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

---

### Post by adventure man on 2022-09-15
[COLOR=#ff0000]**@halogen2**[/COLOR] I tried that and it's still the same error at start.

[COLOR=#ff0000]**@oldfred **[/COLOR]_to your first inquiry_:

```
GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Model: HGST HTS725032A7
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 5C88A4BA-815B-437C-BCC5-9DF63C9DDF5A
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2            4096         1054719   513.0 MiB   EF00  EFI System Partition
   3         1054720       625141759   297.6 GiB   8300  
```


_To your second inquiry_:
"Legacy boot on HDD"

---

### Post by &amp;KyT$0P# on 2022-09-15
> **adventure man said:**
> [COLOR=#ff0000]**@halogen2**[/COLOR] I tried that and it's still the same error at start.

Does the error happen before the GRUB menu appears or only when actually trying to boot Xubuntu?

(If GRUB menu still does not appear, change [FONT=Courier New]GRUB_TIMEOUT[/FONT] to a non-zero number of seconds and again run [FONT=Courier New]sudo update-grub[/FONT] to apply the change)

---

### Post by oldfred on 2022-09-15
Your gpt output is not showing a partition table issue.

But if system is set for UEFI boot, then has to fail & revert to a BIOS/Legacy boot, that may be the issue.
Do you have UEFI settings set to BIOS/LegacyCSM boot mode?
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Most UEFI systems should have UEFI installs.

---

### Post by adventure man on 2022-09-15
[COLOR=#ff0000]**@halogen2:**[/COLOR]
after making the change to GRUB_TIMEOUT like you said, I found that the error occurs *BEFORE* the GRUB menu appears.

---

### Post by adventure man on 2022-09-15
[COLOR=#ff0000]@oldfred[/COLOR]
In the BIOS I see "Boot List Option" with 2 options: Legacy and UEFI. It is set to Legacy.
In "Advanced Boot Options", the setting "Enable Legacy Option ROMs" is checked on.


[B][COLOR=#ff0000]Edit:
I switched the boot list option from Legacy to UEFI and that fixed the problem. Thanks guys![/COLOR][/B]

---

### Post by oldfred on 2022-09-15
Because you have both the bios_grub and an ESP, you can easily convert install from BIOS to UEFI.
The only real difference between UEFI boot & BIOS boot is the version of grub & a few settings that the reinstall of grub also adds.
I used to have both bios_grub & UEFI when first using UEFI, so I could convert, if necessary. Found I did not need it, so now only have ESP. 

If you boot live installer in UEFI mode, so it make UEFI repairs and reinstall grub.
You can chroot, or use Boot-Repair.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by oldfred on 2022-09-15
I would then also check other UEFI settings.
Dell typically used to need many UEFI settings changed.
My new Dell only needed UEFI fast boot off & Windows bit locker & fast start up off. Ubuntu has driver for NVMe drives.
Older Dell also needed drive setting changed from RAID or Intel RST to AHCI.

---

