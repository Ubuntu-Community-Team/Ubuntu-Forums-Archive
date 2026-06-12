---
title: "Adding Windows XP to grub2"
date: 2013-10-17
forum: General Help
---

### Post by GtQXhb8 on 2013-10-17
I've been running Ubuntu 13.04 and Windows 7 dual booted for quite some while now using grub2. I then installed Windows XP. Doing this made Windows XP boot all the time, completely skipping grub. I used Boot-Repair to bring back grub where I can now boot Ubuntu and 7 as I was previously able to. But now I want to add Windows XP to grub so I am able to boot that as well.

I have 1 hard drive with 3 partitions: Windows 7 on sda1, Windows XP on sda2, and then Uuntu. os-prober and update-grub2 do not pick up on the XP installation. I've been trying to add it by adding an entry in /etc/grub.d/40-custom but I can't seem to get that working.

Some help on how to get the 40-custom entry to work or how to get os-prober to pick up on XP would be appreciated.

---

### Post by pqwoerituytrueiwoq on 2013-10-17
when you do a tool/tripple boot with 2+ comes of windows windows will dual boot both copies of windows
grub will wive you ubuntu and windows 7 loader (actually windows 7 or xp, the windows boot loader should ask you which you want to boot)
if windows is not dual booting like that try running [FONT=courier new]sudo update-grub[/FONT]

---

### Post by oldfred on 2013-10-17
Windows puts all its boot files in the partition with the boot flag. So XP probably put its boot files in the Windows 7 partition. But because you installed XP after 7, 7 has not picked up XP to include it in its BCD and XP knows nothing about Windows 7 and BCD to add 7 to its boot.ini.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You may be able to just move the 3 XP boot files to your XP partition. It may need an XP chkdsk or you can use Windows 7 but have to create the older style NTFS partition boot sector. And boot.ini needs to refer to correct partition.

      
 meierfra. - How to fix XP when the boot files are missing + download
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)


 Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

      
 Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by GtQXhb8 on 2013-10-17
Thanks oldfred, meierfra's tutorial worked wonderfully.

---

