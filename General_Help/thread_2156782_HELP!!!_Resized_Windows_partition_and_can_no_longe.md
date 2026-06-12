---
title: "HELP!!! Resized Windows partition and can no longer boot windows"
date: 2013-06-23
forum: General Help
---

### Post by benhorton2 on 2013-06-23
Hi, I was running Windows 7 Home Premium x64 when I decided to give Ubuntu 13 a try. I made a bootable USB drive, and attempted to do a custom install alongside Windows. I had three partitions: dev/sda1, dev/sda2, and dev/sda3. sda1 was for boot, sda2 had the most disk space so I assumed that was where Windows was, and sda3 was HP recovery. I thought if I resized the sda2 partition, I could create a new one on which to install Ubuntu. I assigned that free unpartitioned space to ext3, I believe, ignoring the warning to setup a swap partition. When Ubuntu was installed, it loaded the purple startup screen to choose OS, but Windows 7 did not boot. Panicking, I rebooted from USB and removed ext3 and combined it with the existing sda2 partition. However, that partition is no longer recognized as Windows. When I boot, I get grub loader. Booting from Windows 7 CD and doing Startup Repair failed, the root cause found: No OS files on disk. (Repair action: Partition table repair). I am waiting on a ISO to download so I can burn a 7 disk and attempt to use bootsect.exe to set the MBR to "bootsect /nt60 SYS /MBR" However, I feel this might not work because the boot partition is not the one damaged, but the main one. All of my files are accessible through Ubuntu in the 625 GB Filesystem, so if I have to I'll just back up everything and clean install Windows 7, but if anyone can help me fix it without starting from scratch it would be hugely appreciated!!!

---

### Post by benhorton2 on 2013-06-23
Alright, so I ran bootsect /nt60 SYS /mbr with no avail, said "[COLOR=#323232][FONT=verdana]the system partition was not found: the requested system device cannot be found." I also tried bootrec.exe [/FONT][/COLOR][COLOR=#323232][FONT=verdana]/ScanOS /RebuildBCD [/FONT][/COLOR][COLOR=#323232][FONT=verdana]/FixMBR /FixBoot in that order, and none of them worked. /ScanOS found 1 Windows installation on D:, /RebuildBCD could not add installation to boot list because the specified device cannot be found, /FixMBR and /FixBoot both said the operation completed successfully, but that is unsurprising as it was not the boot sector that was damaged, now the computer boots to Windows Boot Manager instead of grub, saying Windows failed to start... run disk and repair computer. 

but I found a tutorial: [/FONT][/COLOR][http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)
and used "sudo ntfsfix /dev/sda2" which returned:
"Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... FIXED
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed succesfully"

but sudo fdisk -l shows /dev/sda2 to still be System: HPFS/NTFS/exFAT, shouldn't it be NTFS? Restarted the computer and same error screen...

---

### Post by canine828 on 2013-06-23
I think you overwrited the Win7 partition. Re-buy Win7 and put it in a different partition.

---

### Post by benhorton2 on 2013-06-23
i would think you were right, as most signs point to sda2 having been overwritten, but check out the results from running a boot repair disk:
[http://paste.ubuntu.com/5792110/](http://paste.ubuntu.com/5792110/)
It clearly shows the operating system Windows 7 being installed on sda2, only with the extra boot files for wubildr.
Unfortunately, after the attempt to repair, it still won't boot and the log looks no different:
[http://paste.ubuntu.com/5792167/](http://paste.ubuntu.com/5792167/)
Plus, all of my files are accessible at the root of the hard drive within Linux
But according to it, the MBR of Syslinux is installed upon dev/sda, so all the boot loader changes I've tried to make through Microsoft and Ubuntu have been ineffective.
However, the results of "sudo os-prober" indicate that dev/sad2 and dev/sda3 are both "Windows Recovery Environment (loader):Windows:chain", which should only be true of sda3 as it is the HP recovery partition.
I think if I can just make sda1 realize it needs to boot sda2, that everything would work again
Since I restarted my computer last, gparted shows sda2 (which wouldn't mount before) is now mounted at /media/ubuntu/A820658F206564F2 and it shows it's locked
I hope this information helps, I would really appreciate it if someone could assist, I really don't want to reinstall Windows 7

---

### Post by Mark Phelps on 2013-06-23
You should seriously consider visiting the Windows 7 forum (sevenforums.com) and posting there -- if your initial focus is to get Win7 working again.  They have tutorials for doing repairs.  Also, they have a tutorial for doing a refresh of Win7 -- provided you have installation media -- that will not overwrite your apps, data, or files.

---

### Post by lokex on 2013-06-23
If your resized partition mounting without any errors, you can boot with the Windows 7 disk, or if your system comes with a one-button recovery, run that. If you boot with a windows 7 disk, and choose to repair, it may fix your problem. 

Windows based recovery is your only option.

---

### Post by benhorton2 on 2013-06-23
alright, thanks for the replies, i guess i have no choice but to back up everything and start fresh, there was no way to repair the partition through the Windows CD so I will have to erase all data, plus I probably did irreversible damage using testdisk and universal boot cd so whatever a clean slate it is!

---

### Post by oldfred on 2013-06-23
You have boot flag on sda1, but only one of the two files required to boot. You need the /boot/BCD in sda1, but only have one in sda2.
You can either add the BCD to sda1 or move boot flag to sda2. In Windows I believe the command is makeactive, but do not use Windows.

---

