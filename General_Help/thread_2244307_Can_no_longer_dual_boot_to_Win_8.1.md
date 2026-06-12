---
title: "Can no longer dual boot to Win 8.1"
date: 2014-09-15
forum: General Help
---

### Post by Josef Lauri on 2014-09-15
I bought an MSI GEO-60-2PC laptop with Win 8.1 pre-installed. I installed Ubuntu 14.04 with partitioning of the 1TB HD as 250MB for Win and 750MB for ubuntu. It worked fine. On powering up I got the grub screen, and could choose which OS to use. Then, suddenly I could no longer boot into Windows (ubuntu is still booting fine). When I try Windows  gives me messages that it is trying to repair the pc, but it gives up. I ran boot-repair but I still have the same problem. boot-repair gave me this url to quote: [http://paste.ubuntu.com/8350528/](http://paste.ubuntu.com/8350528/)

Thank you for any help you can provide.

Josef

---

### Post by oldfred on 2014-09-15
I do not see anything in the report that looks out of place.

But grub really only boots working Windows.
Did you leave Windows fast boot or always on hibernation on? And it tries to reset it to defaults or on regularly.

You may need your Windows repair disk to fix Windows. 
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Typically Windows also has the repairs in the boot partition or your sda1. If you press f8 at almost the same time as the entry in grub you may be able to get to Windows repair console. If not use boot repair to temporarily install a Windows boot loader to the MBR, so you then can use f8 as that has a bit longer time. Then restore grub using Boot-Repair after you have fixed Windows.

      
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by Josef Lauri on 2014-09-16
Thanks oldfred. I'll try out your suggestions with the help of a friend who is more technical than I am. I can live with only ubuntu loading, but I do not want to lose that. 
Thanks.
j

---

