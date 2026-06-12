---
title: "HP UEFI BIOS Resetting"
date: 2015-03-02
forum: General Help
---

### Post by pgp_protector on 2015-03-02
System Information
HP Envy 700-074 12G System With Windows 8.1 Preinstalled 

1) Added New 3TB SATA Harddrive to System (3rd HD In system)
2) Disabled Secure Boot in BIOS
3) Boot UBUNTU 14.04 x64 Live CD, and Install OS
4) After Install, Reboot system, system boots to Windows, no Option for Linux.

Then
5) Reboot to Live CD, and use the Boot Repair Tool [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
6) Enter BIOS , set Boot Order -> UBUNTU.  Disable Windows, Disable USB CD, Disable USB HD  Save & Power Down.
7) Power up system, GRUB Shows as expected.  Able to run UBUNTU as expected.
8) Reboot, GRUB Shows, Select Windows  (Now the problems start)
9) Windows Boots as expected & is usable
10) Reboot, and Boots to Windows, No GRUB again
11) CHECK BIOS (Boot Order is set back to Windows, & It's Enabled, USB Devices Still Disabled, Ubuntu Enabled, but on bottom of list)

Long story Short.  Windows is Resetting the BIOS and forcing BOOT DEVICE to Windows.  Has anyone seen this?, and if so did you fix it (If so, How? )

Thank you for your help.
PGP_Protector.

---

### Post by oldfred on 2015-03-02
Standard with HP and many other vendors.

The UEFI standard says you should be able to boot any entry. But vendors modify UEFI to only boot Windows. Some will work with the UEFI one time reboot entry and for those you can edit BCD in Windows. But that requires a reboot.

Most edit the hard drive boot entry which at least for now still works.  Then in UEFI you can directly boot hard drive, but we make that file bootx64.efi really be grub.

Since a different drive did you also include an efi partition on that drive. I prefer to make each drive bootable without any others. When I installed to my second drive, the installer defaulted grub2's efi files to my first drive' efi partition, and I am pretty sure I specified the correct drive. But I then just copies efi boot files to efi partition on second drive.

          Backup entire efi partition before making changes.
         A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot
          Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
     Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)
         From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
         sudo mount /dev/sda1 /mnt
         only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
         If new folder created, the bootx64.efi will not exist, skip backup command
             sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
         make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
             sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by pgp_protector on 2015-03-03
> **oldfred said:**
> Standard with HP and many other vendors.

The UEFI standard says you should be able to boot any entry. But vendors modify UEFI to only boot Windows. Some will work with the UEFI one time reboot entry and for those you can edit BCD in Windows. But that requires a reboot.

Most edit the hard drive boot entry which at least for now still works.  Then in UEFI you can directly boot hard drive, but we make that file bootx64.efi really be grub.

Since a different drive did you also include an efi partition on that drive. I prefer to make each drive bootable without any others. When I installed to my second drive, the installer defaulted grub2's efi files to my first drive' efi partition, and I am pretty sure I specified the correct drive. But I then just copies efi boot files to efi partition on second drive.

Both Drives have a EFI Partition already.

In BIOS I can Boot from either Drive when they're set to be the Boot Drive.

> **oldfred said:**
> 
          Backup entire efi partition before making changes.
         A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot
          Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
     Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)
         From live installer mount the efi partition on hard drive, lines with # are comments only: Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
         sudo mount /dev/sda1 /mnt
         only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
         If new folder created, the bootx64.efi will not exist, skip backup command
             sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
         make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
             sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

When I Cycle Power, as Long As I haven't booted to windows, GRUB will show up (So it's booting of the 3rd HDD )
Once Windows boots though Windows is modifying the HP BIOS to make the Windows Drive the Boot Drive, even if in the BIOS the Windows Drive is Disabled as a boot drive.

Will take photos soon.

---

### Post by oldfred on 2015-03-03
Are you using ubuntu entry in UEFI. As Windows will change that.

But I thought it would not change the hard drive entry. But Windows syncs BCD with UEFI and that causes issues.

---

### Post by pgp_protector on 2015-03-03
> **oldfred said:**
> Are you using ubuntu entry in UEFI. As Windows will change that.

But I thought it would not change the hard drive entry. But Windows syncs BCD with UEFI and that causes issues.

Yes I set UBUNTU in UEFI, and Disable the Windows Entry in UEFI.
As long as I don't boot to windows, I can cycle power as much as I want, and the BIOS will use the UBUNTU GRUB.

But once I select Windows, the BIOS itself is changed, and I have to go back into the BIOS to get ubuntu selected as the Boot Drive.

Got the question also sent into HP Support (It's one of their boxes)  I just want to get the BIOS "Locked" from changes.  And the thought that an OS Can change the BIOS Settings is a bit disturbing in reality.

---

### Post by oldfred on 2015-03-03
Try editing bootx64.efi and set hard drive as boot choice.

I also have seen this suggested. But I think you have to boot into Window to load BCD, then it reboots using UEFI one time reboot option to "let you" boot something else than Windows.

 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by pgp_protector on 2015-03-03
> **oldfred said:**
> Try editing bootx64.efi and set hard drive as boot choice.

I also have seen this suggested. But I think you have to boot into Window to load BCD, then it reboots using UEFI one time reboot option to "let you" boot something else than Windows.

 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

Ok the command from windows (bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi)
"Fixed" the issue, well at least it allows me to load the GRUB & select my OS.

Still don't like that Windows is changing my BIOS though.

---

