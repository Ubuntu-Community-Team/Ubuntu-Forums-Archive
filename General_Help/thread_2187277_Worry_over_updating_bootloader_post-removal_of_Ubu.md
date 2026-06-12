---
title: "Worry over updating bootloader post-removal of Ubuntu 12.10 from dual-boot W8 system"
date: 2013-11-11
forum: General Help
---

### Post by adnek.spider on 2013-11-11
Ok, I have already trawled through forums and although there have been other posts similar to this I feel I need to add some detail regarding my particular irritation.

I installed Ubuntu 12.10 on a system already having Windows 8 - the Ubuntu partition was created during install. I then had to 'fix' the bootloader after install because I couldn't get back into Windows. That fix worked and all was hunky dory until I forgot my Ubuntu password. Again went to the forums and followed instructions to change my root password for my username via the Ubuntu Advanced Options. After 'successful password change' I tried to continue boot into normal Ubuntu but it froze and I ended up manually switching off my computer and turning it back on again. When I got to the Ubuntu log-in screen it decided to lock me in a loop, switching between a black screen and the log-in one whenever I entered my new password. Again forums, but their fixes didn't solve the problem and I am now wanting to take off this installation of Ubuntu, de-partition if need be, and reinstall it. 

The last time I dual-booted Ubuntu with Win8 and needed to uninstall Ubuntu, I could just remove it in Windows as if it were a program. This time round however, 'Ubuntu' is nowhere to be found in the Programs list. Any ideas why one time and not another? The first time Ubuntu was installed via a Live USB and this time via a Live DVD, though not sure why that would make a difference. Anyway, new plan...

Using my Live DVD I am 'trying' Ubuntu and I have downloaded and run OS-uninstaller. When it gets to the 'which OS do you want to unistall' bit, I have three options: 
[LIST=1]
[*]Windows Recovery Environment (boot) (sda3) 
[*]Windows 8 (sda5) 
[*]Ubuntu 12.10 (sda8) 
[/LIST]

I selected the ubuntu one and got the following:[INDENT][B]This will remove Ubuntu 12.10 (sda8).
Then you will need to update your bootloader.
Apply changes?[/B]
This partition will be formatted, please backup your documents before proceeding.
[/INDENT]

That is all as expected, bar the updating my bootloader bit. I am worried that if I now remove Ubuntu I won't be able to get back into Windows, I am assuming because of the boot-loader fix I did post-install. I do not currently have a Windows recovery disc on hand and if possible, I would like not to have to use one. I need to get my Ubuntu back up and running ASAP for work.

Advice?

---

### Post by oldfred on 2013-11-11
It sounds as if you may have had wubi before. It is being discontinued as it does not work with gpt partitioned drives which new Windows 8 pre-installed systems all have.

If you have UEFI you should be able to directly boot Windows from UEFI menu and from UEFI menu make sure Windows is the first boot option. With BIOS installs you would have to make sure you have a Windows boot loader in the MBR of the MBR(msdos) partitioned drive.

How you boot install media is how it installs. If you system is UEFI review the many (too much info?) links in the link in my signature.

Also best to have good backups of efi partiton and Windows main install and a Windows repairCD or flash drive.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

