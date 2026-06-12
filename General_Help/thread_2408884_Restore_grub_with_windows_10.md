---
title: "Restore grub with windows 10"
date: 2018-12-24
forum: General Help
---

### Post by mypmeow on 2018-12-24
Hi all. I have a problem with my grub, he not have "windows 10" in menu. How I can restore this menu? Bootrepair - not help me. Thanks!

---

### Post by ajgreeny on 2018-12-24
It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below but this time follow the instructions there to run the Boot-Info-Script.	 **Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by mypmeow on 2018-12-26
Thanks for you reply.
My PC-info: [http://paste.ubuntu.com/p/pg6HhxHbMj/](http://paste.ubuntu.com/p/pg6HhxHbMj/)

---

### Post by yancek on 2018-12-26
You have windows partitions on both drives, which one has the windows 10 system files?  Your first drive with Ubuntu is GPT and your second drive is Legacy/msdos and has windows on it.

You have 3 EFI partitions on the first drive and only one is allowed/needed.  sda3 and sda7 show EFI files for Manjaro but there is no other sign of Manjaro.  Did you remove/format that partition?  If you no longer have Manjaro installed, you could delete or format those partitions.

Mixing Legacy installs with EFI installs is usually problematic.  Have you tried running:  sudo update-grub from Ubuntu?  Are you actually able to boot Ubuntu?
You could try creating the BIOS-Boot partition, 1MB unformatted with GParted which should be on the Ubuntu install disk as suggested in boot repair.

---

### Post by mypmeow on 2018-12-26
I write now from ubuntu. Windows 10 on other disk it is older and not user Windows. I need restore grub for windows how store on sda4.
Manjaro I delete, I use ubuntu and not use manjaro. I want grub menu with Windows 10 (sda4) and Ubuntu (sda6).
Update-grub - i tried, it's not help for me. 
Thanks for reply!

---

### Post by oldfred on 2018-12-26
While you have 3 FAT32 partitions with UEFI boot files, none have the boot/esp flags to set it as the ESP - efi system partition. A very few have multiple FAT32 partitions and move boot flag to boot another install, normally only when installs are not compatible.

Use gparted and add boot flag to sda2. Ubuntu then should boot in UEFI boot mode.

But you show no Windows boot files at all for UEFI boot in any of the FAT32/old ESPs. You must have erased the ESP with Windows boot files. You have to run a full set of Windows repairs from a Windows installer's repair console or your Windows repair flash drive.
If you do not have either, it is easier to buy a new flash drive and create a new repair flash drive from another Windows system (any Windows 10 64 bit).
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

You then also have to turn off Windows fast start up for grub update to find the Windows install. Grub only boots working Windows, so keep Windows repair flash drive. Windows will turn fast start up back on with updates & make itself first in UEFI boot order. (Grub also makes itself first on major updates).
       
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

