---
title: "how to upgrade MS Windows disk?"
date: 2016-10-06
forum: General Help
---

### Post by davidmaxwaterman on 2016-10-06
Hi,

I have a system that is primarily Ubuntu and uses grub to boot. I also have a disk on it that has Windows on it. It seems like I need to have a windows boot loader on it in order to upgrade windows, so I figured I'd unplug all my other disks and work on just that disk; but it doesn't seem to boot.

Can someone advise me how to boot to just windows? Is there an easier way?

---

### Post by yancek on 2016-10-06
Which windows version?  UEFI or MBR?  Is this a new setup, did it ever work to boot both Ubuntu and windows?  Best next step is to go to the site below and get the boot repair software.  Download and run it per instructions selecting the option to Create BootInfo Summary and post a link to the output here so more details are available for members to make suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by davidmaxwaterman on 2016-10-06
I think it's Windows 7. It can boot into either - by default it goes into Ubuntu but I can select Windows from the grub menu, and it works fine. It's just that Windows needs its own boot loaded to upgrade...iinm.

---

### Post by davidmaxwaterman on 2016-10-06
[http://paste2.org/Db7I3hDK](http://paste2.org/Db7I3hDK)

Any clues in there?

---

### Post by Jimysbil on 2016-10-06
As long as it boots with grub I assume you should have not problem to boot it without grub.If you have a separate Windows Hard disk only for Windows the only logical explanation is you have not MBR bootcode installed on your MBR or the partition with your Windows bootloader (probably System Reserved partition) is on an other disk.

A probable fix would be to boot in your Windows with Grubs help.In case you have MBR partition table just open a cmd prompt and type the command:
```
bootsect /nt60 {your windows partition letter}: /mbr
```
This command should rewrite your Windows MBR bootcode to your Windows disk.

If you are using UEFI you could type the command:
```
bootrec.exe  /fixmbr
```
* But I don't know if this command will fix your boot on your current disk or it will fix your boot on the disk you booted from.

But if it is easy for you get into ubuntu and execute the commands:
```
sudo su
fdisk -l
blkid
```
and copy-paste the results here in order to give us more informations about your partitions and your partition table.

---

### Post by oldfred on 2016-10-06
Boot-Repair or your Windows repair disk can install a Windows boot loader to your current sdf drive. I would have always had a Windows boot loader in that drive. Boot-Repair installs the syslinux boot loader which is a BIOS type boot loader similar to Windows' official one. 

Before major upgrade I would still make a full backup of Windows. And a Windows repair disk.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader
[/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 

      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
    [       ]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) 

 Then as soon as you have new Windows working well, back it up & create its version of repair disk.

---

### Post by davidmaxwaterman on 2016-10-06
ok, thanks guys. Some things to be getting on with there :D

Thanks again!

---

