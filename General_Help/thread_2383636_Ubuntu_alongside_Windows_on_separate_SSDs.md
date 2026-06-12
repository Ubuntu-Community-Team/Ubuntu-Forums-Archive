---
title: "Ubuntu alongside Windows on separate SSDs"
date: 2018-01-27
forum: General Help
---

### Post by alex495 on 2018-01-27
[COLOR=#000000][FONT=Calibri] I have 2 SSDs on my machine, one a Samsung 840 Evo with Windows 8.1  installed on it, and another a Samsung 960 Evo OEM NVME disk with  Ubuntu 16.04 installed. Unfortunately GRUB doesn't seem to have installed properly (I recall it automatically took over from the Windows boot manager when I installed Windows and Ubuntu on the same disk) and I can't boot to Ubuntu. I've read a tutorial found [here]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") that recommends repairing grub by going using chroot into the system from a live Ubuntu USB, but got stuck at the step where I install/update grub. I type in ```
sudo grub-install /dev/mapper
``` (I believe I have an LVM installation) and get an error claiming fopen has hailed as it can't open /devices/proc. This error repeats several times, and is followed by another saying an attempt was made to read outside the host disk. Basically I'm stuck at this point as I'm pretty new to this and don't know how to troubleshoot further. Any help would be really appreciated.

 

 [/FONT][/COLOR]

---

### Post by C.S.Cameron on 2018-01-27
Is the Ubuntu disk the first HDD in your BIOS / UEFI?

---

### Post by alex495 on 2018-01-27
> **C.S.Cameron said:**
> Is the Ubuntu disk the first HDD in your BIOS / UEFI?
Actually, the BIOS doesn't seem to see my Ubuntu disk. It's NVME and my motherboard doesn't technically support it. I modded the BIOS with the required .ff package for NVME support, but it still doesn't show up in bootable devices (a tutorial I followed [here]("https://www.win-raid.com/t871f50-Guide-How-to-get-full-NVMe-support-for-all-Systems-with-an-AMI-UEFI-BIOS.html") indicated that that's normal even though it should be bootable).

---

### Post by oldfred on 2018-01-28
The default install with UEFI of grub is into the ESP - efi system partition on the drive seen as sda.
So grub would be in same ESP as Windows on SSD, not on NVMe drive.

If encrypted mount & unencrypt your LVM before running report.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by alex495 on 2018-01-29
Here is the report: [http://paste.ubuntu.com/26481846/](http://paste.ubuntu.com/26481846/)
The final portion of the report contains some advice on actions to perform, specifically reinstalling grub2 to the MBR of the other disk. I'll try exploring that route, but it also claims that I'll need to set the system to boot from the NVME disk, and I don't know if I can do that since BIOS isn't showing the disk in the boot menu.

---

### Post by oldfred on 2018-01-29
When you have multiple drives, and the now 35 year old BIOS/MBR install, I suggest keeping Windows boot loader on Windows drive and Ubuntu bootloader (grub) on Ubuntu  drive.
Grub only boots working Windows. Or Windows that is not hibernated, nor corrupted and needing chkdsk. So sometimes you need to directly boot Windows as it turns on fast start up/hibernation in back ground with major updates and sometimes needs chkdsk. Then you have to directly boot Windows or use your Windows recovery/repair flash drive.

With newer UEFI both boot loaders share the ESP - efi system partition on the first drive. So Windows can be directly booted from UEFI when it needs to be directly booted.

But with your adapters to make NVMe work, not sure if your only choice is to install grub to sda. And then have both Ubuntu live installer (so you can add Boot-Repair) and a Windows repair flash drive. Boot-Repair cannot do most Windows repairs.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options

[/URL]
 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/)
WinRE recovery partition after main NTFS
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 

[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

