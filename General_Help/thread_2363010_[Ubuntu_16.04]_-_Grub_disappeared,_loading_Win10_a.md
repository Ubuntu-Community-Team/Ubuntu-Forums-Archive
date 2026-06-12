---
title: "[Ubuntu 16.04] - Grub disappeared, loading Win10 automatically"
date: 2017-06-05
forum: General Help
---

### Post by carlo8 on 2017-06-05
Hi guys, I'm experiencing a strange issue.
I have a dual boot with Ubuntu 16.04 and Windows 10, worked perfectly so far.
Yesterday, I simply rebooted the system from Ubuntu and started Windows...after that, I rebooted again to load Ubuntu, but I didn't get the initial GRUB screen, and the laptop has been automatically loading Windows since.

I used the Ubuntu Live version from a USB stick, installed the boot repair tool and selected "recommended repair". At the end of the process, I got this message:

```

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB-200MB, start of the disk, boot flag). This can be performed via tools such as gParted.
Then select this partition via the [Separate/boot/efi partition:] option of [Boot Repair]

```

But I already have the EFI boot partition at /sda1, with the boot flag active (I checked from gParted).
I started BootRepair again, and in the advanced options - GRUB location the "Separate/boot/efi partition: sda1" option is already checked.

Any suggestions, please?



EDIT: ok, I ran the BootRepair once again and this time it worked, I have the GRUB menu again and I can load both Win10 and Ubuntu.
Just, now on the GRUB menu there are many more options than before (I used to have only the ones I wrote in bold):

```

[I][B]Ubuntu
Advanced options for Ubuntu
[/B][/I]Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
EFI/ubuntu/fbx64.efi
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi
EFI/HP/BIOSUpdate/CryptRSA.efi
EFI/HP/BIOSUpdate/HpBiosMgmt.efi
EFI/HP/BIOSUpdate/HPBiosUpdate.efi
EFI/HP/SystemDiags/CryptRSA.efi
EFI/HP/SystemDiags/HPSysDiags.efi
EFI/HP/SystemDiags/SystemDiags.efi
[I][B]Windows Boot Manager (on /dev/sda1)
System Setup[/B][/I]

```

any clue as why?

---

### Post by oldfred on 2017-06-05
Windows updates run in background. 
And many of them, like major updates to grub reset UEFI boot order.

The first time you ran Boot-Repair either ESP was mounted with restricted permissions or needed dosfsck.
Newer versions of Ubuntu changed mount of ESP from defaults to umask=0077perhaps for secuity? I change mine back to default do I can backup & edit entries as I have multiple Ubuntu installs and need access.

HP also is not dual boot friendly. Most HP will not let you set Ubuntu as default and keep it for more than one use. They modify UEFI to use description as part of boot and only valid description is "Windows Boot Manager". That is not allowed per UEFI spec.
Users either use the UEFI one time boot key to get to UEFI menu and choose ubuntu entry or create the fallback or hard drive entry and that still seems to be allowed as a default entry.
Boot-Repair now copies /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi as the fallback. Do you already have an UEFI boot entry for hard drive? And does it boot Ubuntu, if you ran Boot-Repair. With many HP, entry is there but it is just another copy of Windows .efi boot file.

Also Boot-Repair sees all the HP .efi files in /EFI and adds them to grub menu. Most are not required to be in grub menu and you can edit or delete the 25_custom file in grub that has those entries. Details in link in my signature.

---

