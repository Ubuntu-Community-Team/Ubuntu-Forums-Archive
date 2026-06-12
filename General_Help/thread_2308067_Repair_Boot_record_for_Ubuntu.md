---
title: "Repair Boot record for Ubuntu"
date: 2015-12-30
forum: General Help
---

### Post by jernej-jerin on 2015-12-30
Hi!

I had a dual boot of Ubuntu/Windows 10. I then decided that I want to get rid of Windows 10, and followed [official documentation]("https://help.ubuntu.com/community/HowToRemoveWindows") for removing Windows boot. I used OS-Uninstaller Graphical Tool from Ubuntu live CD. At the end there was error displayed about operation not finishing successfully. I restarted and now the GRUB menu does not appear anymore, hence I cannot boot into Ubuntu anymore. I have Secure Boot disabled, and set boot menu to UEFI and CSM mode, just as I had before I removed Windows. Under LiveCD I tried to repair GRUB by using [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). I selected Recommended repair and the following error appears:[INDENT]
[I]GPT detected. Please create a BIOS-Boot partition (> 1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

[/I][/INDENT]
I tried to created partition named BIOS-Boot in Gparted, set the following under option for Create a new Partition:


[LIST]
[*]Free space preceding (MiB): 1
[*]New size (MiB): 1
[*]Free space following (MiB): 194196
[*]File system: unformatted
[*]Label: BIOS-Boot
[/LIST]
When I Apply all operations, the File system is changed to NTFS (not sure if this is alright?). I then set the flag to bios_grub for this partition (/dev/sda1). So now I have the following partitions:
[LIST]
[*]/dev/sda1 (ntfs), the partition I just created with bios_grub set under Flags
[*]/dev/sda5 (ext4), it says Mount-Point: /mnt/boot-sav/sda5, so this is the main partition where Ubuntu is installed
[*]/dev/sda6 (linux-swap)
[/LIST]
I rerun the Boot repair and **still get the same error as before! **I have created the BootInfo summary, which is [available here]("http://paste.ubuntu.com/14292982"). As you can see it has this line: [COLOR=#000000]/dev/sda1           2,048         4,095         2,048 BIOS Boot partition. So why does this not work. What is wrong, how can I fix this?[/COLOR]

---

### Post by grahammechanical on 2015-12-30
> The boot of your PC is in EFI mode, but no EFI partition was detected.

Ubuntu has been installed in BIOS/Legacy/Compatibility mode. You need to boot in BIOS/Legacy mode to load the Ubuntu boot loader. That is my guess.

Or, when you removed Windows 10 you also removed the partition that held the Windows 10 efi boot files and the Ubuntu efi boot files.

Regards.

---

### Post by jernej-jerin on 2015-12-30
I tried to boot in CSM mode, which is BIOS legacy mode, but it did not make any difference. I think the second reason might be true, as I did install Ubuntu next to Windows 10, so OS-Uninstaller probably deleted Ubuntu efi boot files when removing Windows boot.

---

### Post by jernej-jerin on 2015-12-30
Was just checking about UEFI boot partition and come across fstab. This is from /dev/sda5:[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=7980ad06-360e-43ba-b942-3c72a940a280 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=369F-0BB6  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda6 during installation
UUID=3098baac-6f83-4305-9522-ee4fd85c46b1 none            swap    sw              0       0
UUID=369F-0BB6    /boot/efi    vfat    defaults    0    1[/INDENT]
I guess this explains, right: **/boot/efi was on /dev/sda2**. But how do I now fix this, or that the Boot Repair will be able to fix it?

---

### Post by oldfred on 2015-12-30
What was sda1? 
The bios_grub needs to be unformatted and only 1 or 2MB. It can be anywhere on drive. It is only requried on gpt partitioned drives if you want to boot in CSM/BIOS/Legacy boot mode.
Most newer systems use UEFI and need an ESP - efi system partition which must be FAT32 with boot flag.

Best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If need to always boot in UEFI mode if system is installed in UEFI mode, including Boot-Repair or Ubuntu live installer to make repairs.
When you boot live installer if you get grub menu then you are in UEFI mode. If you get purple accessibility screen with tiny icons at bottom then you are in BIOS mode.

---

### Post by jernej-jerin on 2015-12-31
@oldfred, I have the option UEFI & CMS mode in BIOS options, therefore I get GRUB menu. I have posted the link to BootInfo summary in first post. The /dev/sda1 is what I created, hopefully that Boot Repair would then stop reporting problem that I quoted in first post.

---

### Post by oldfred on 2015-12-31
The Boot-Repair issue is probably that you booted it in BIOS mode so it was trying to reinstall grub in BIOS mode and then grub wanted the bios_grub partition.
If in UEFI mode, you do not need bios_grub partition and grub-efi-amd64 should reinstall without issue.
You must at some point reinstalled grub in UEFI mode as Boot-Repair comments out (#) original mount of efi partition and added a new one. Note different permissions. If running Boot-Repair from inside your install, the 0077 prevents any writing to ESP. But defaults will allow you to add or correct entries. Not sure why they changed from defaults in older installs to 0077 in newer ones??

---

### Post by jernej-jerin on 2016-01-02
I have managed to fix GRUB by following this [first three steps]("http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi"). After that I reran Boot-Repair and it managed to repair the boot. Thank you all!

---

