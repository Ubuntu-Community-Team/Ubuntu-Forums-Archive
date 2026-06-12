---
title: "Boot problems, corrupted files or faulty GRUB"
date: 2020-01-21
forum: General Help
---

### Post by vellofrell on 2020-01-21
Hi all - I'm in a bind and curious on suggestions. I have been looking for solutions for days and found nothing that works. 

Back story - I tried to clone my boot OS drive to another drive inside the same machine. After this, I cannot properly boot up my server machine. It always boots only Emergency Mode. I can see through the Terminal however that my OS file system appears generally intact.

After running 'journalctl -xb' from Emergency Mode, I see listed in red something along the lines of "couldnt get size MODSIGN couldnt get UEFI db list."

I don't yet understand if this is a faulty grub bootloader issue, or if part of the internal filesystem has become corrupted. Any ideas on where to start? I'd really love to not need to start fresh with a clean install.

[COLOR=#242729][FONT=Arial]A) Ubuntu Server 18.04.3 / Kernel version 4.15.0-74 generic[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]B) Server[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]C) Boot drive is Samsung 850 EVO 250GB 3D V-NAND SATA III 6GB/s 2.5" Internal Solid State Drive. Backup drive, cloned from Samsung 850 EVO to this one is Seagate IronWolf ST6000VN0041. I have since removed this drive from the machine. One other similar Seagate drive remains inside the machine, containing my trove of files.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]D) Best of my knowledge, source drive that will now not boot is UEFI.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]E) Destination drive - not sure of UEFI or Legacy. This is where it gets over my head.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]F) Tried to clone with Rescuezilla/ReDo Backup bootable USB. Had cloned to an external portable drive, and attempted to restore to above-mentioned Seagate Ironwolf drive. This is when my problems began.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]G) sudo parted -l shows the following Number Start End Size File System Name Flags 1 1049kB 538 MB 537 MB fat32 EFI System Partition boot,esp 2 538 MB 1305 MB 768 MB ext2
3 1305 MB 250 GB lvm[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]..Worth mentioning that "lvm" thing was one of the first error messages being flashed at me upon trying to reboot on Sunday morning.[/FONT][/COLOR]

---

### Post by oldfred on 2020-01-21
Do not know LVM nor Server installs.

But if cloning, you cannot keep both drives plugged in. Duplicate UUID/GUIDs are not allowed. If you want to keep both drives, you have to edit all UUIDs on one drive & reinstall grub.
Often easier just to do a new install & restore your data from your backups as you would do if you had a hard drive crash. Becomes a good test as you still have old drive in case backup was not as good as your thought.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vellofrell on 2020-01-22
Hi - I am now able to boot up, thankfully. Someone suggested I make certain to revise my /etc/fstab file. That got my server up and running again. 

When running 'journalctl -xb' I still have red-font items like these: 

Jan 22 18:19:02 server kernel: Couldn't get size: 0x800000000000000e
Jan 22 18:19:02 server kernel: MODSIGN: Couldn't get UEFI db list
Jan 22 18:19:02 server kernel: Couldn't get size: 0x800000000000000e

and these: 

Jan 22 18:19:02 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 22 18:19:02 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 22 18:19:02 server kernel: No Arguments are initialized for method [_GTF]
Jan 22 18:19:02 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 22 18:19:02 server kernel: ata5.00: supports DRM functions and may not be fully accessible
Jan 22 18:19:02 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 22 18:19:02 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 22 18:19:02 server kernel: No Arguments are initialized for method [_GTF]
Jan 22 18:19:02 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 22 18:19:02 server kernel: ata5.00: disabling queued TRIM support
Jan 22 18:19:02 server kernel: ata5.00: ATA-9: Samsung SSD 850 EVO 250GB, EMT03B6Q, max UDMA/133
Jan 22 18:19:02 server kernel: ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Jan 22 18:19:02 server kernel: ata4.00: ATA-10: ST12000NM0007-2A1101, SN02, max UDMA/133
Jan 22 18:19:02 server kernel: ata4.00: 23437770752 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 22 18:19:02 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 22 18:19:02 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 22 18:19:02 server kernel: No Arguments are initialized for method [_GTF]
Jan 22 18:19:02 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 22 18:19:02 server kernel: ata5.00: supports DRM functions and may not be fully accessible
Jan 22 18:19:02 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 22 18:19:02 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 22 18:19:02 server kernel: No Arguments are initialized for method [_GTF]
Jan 22 18:19:02 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT3._GTF, AE_NOT_FOUND (20170831/psparse-550)



Curious on suggestions to troubleshoot these errors?

---

### Post by oldfred on 2020-01-22
Modsign is related to UEFI settings for Secure boot.

MODSIGN: Couldn't get UEFI db list
From different grub install error.
[https://bugzilla.redhat.com/show_bug.cgi?id=1497559](https://bugzilla.redhat.com/show_bug.cgi?id=1497559)
Change UEFI settings from custom to standard
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700) &
[https://ubuntuforums.org/showthread.php?t=2407705](https://ubuntuforums.org/showthread.php?t=2407705)


[https://askubuntu.com/questions/1095766/ubuntu-bootable-drive-couldnt-get-size-0x800000000000000e-modsign-couldnt](https://askubuntu.com/questions/1095766/ubuntu-bootable-drive-couldnt-get-size-0x800000000000000e-modsign-couldnt)

---

### Post by rescuezilla on 2020-02-27
As noted above, the issue here was solved (after a [post]("https://sourceforge.net/p/redobackup/discussion/1169664/thread/f954e803b5") on the Redo Backup Sourceforge forum). The cause was a device listed in /etc/fstab no longer being present, causing the Linux boot to drop into systemd Emergency Mode.
[QUOTE=rescuezilla]
[COLOR=#555555][FONT=Lato]Hi Vello Frell,[/FONT][/COLOR]
[COLOR=#555555][FONT=Lato]My understanding is you have done the following[/FONT][/COLOR]

[LIST=1]
[*]Used Rescuezilla v1.0.5 to backup your boot drive onto an external harddrive.
[*]Used Rescuezilla v1.0.5 to restore this image onto a third harddrive within in your machine
[/LIST]
[COLOR=#555555][FONT=Lato]If those are indeed the operations that you did, your original boot disk should not have been modified in anyway.[/FONT][/COLOR]
[COLOR=#555555][FONT=Lato]Looking into your exact error message, random [forum]("https://forums.opensuse.org/showthread.php/535324-MODSIGN-Couldn-t-get-UEFI-db-list?p=2897520#post2897520") [topics]("https://bugzilla.redhat.com/show_bug.cgi?id=1497559") for Linux distributions unrelated to Ubuntu suggest there is a bug with Linux kernel 5.0 where the kernel integrity checker attempts to import UEFI certificates at a non-existant memory address.[/FONT][/COLOR]
[COLOR=#555555][FONT=Lato]Could it be that you updated your Linux kernel on your server and this is your first reboot in a significant amount of time so that GRUB is booting using a new Linux kernel that you never actually used before? The first way to check is to boot with a previous Linux kernel from your GRUB menu. Some solutions in those threads suggest disabling Secure Boot in the BIOS and rebooting, but I think first select an old Linux kernel using GRUB to test.[/FONT][/COLOR]
[COLOR=#555555][FONT=Lato]By the way, as you may know modern systemd Linux environments such as Ubuntu 18.04, the partitions listed in the /etc/fstab file must be present for the system to complete booting. If this is not the case (such as due to your third hard drive being reformatted or removed) your system will enter Rescue Mode until the /etc/fstab is modified to only refer to the drives which are present in the system. You are in Emergency Mode, so are not in this situation (yet), but it's something that you may encounter once you fix your current issue. (Note: Fixing a machine in this situation requires remounting the root partition as read/write, then modifying /etc/fstab to remove the line with the hard drive UUID that's no longer present, then remounting the root partition as read-only before hard rebooting the machine. There's plenty of guides on the internet for that particular issue)[/FONT][/COLOR][/QUOTE]
[QUOTE=vellofrell][COLOR=#555555][FONT=Lato]Oh my gosh - thank you for clarifying the part about the /etc/fstab config. I can now succesfully boot up my server. Cheers.[/FONT][/COLOR][/QUOTE]
Can the forum topic please be edited to start with [SOLVED]?

---

### Post by dragonfly41 on 2020-02-27
[COLOR=#000000]> Can the forum topic please be edited to start with [SOLVED]?

This requires the "original poster" velofrell (owner of this thread) to go to top of this page and use "Thread Tools".[/COLOR]

---

