---
title: "Grub boot problem (Win 10+ubuntu)"
date: 2017-02-18
forum: General Help
---

### Post by karlicka1 on 2017-02-18
Hey guys,

I've tried to install ubuntu on a different disk than my Windows 10 SSD with the grub boot selected for the system disk. 

Now I cannot access Windows 10 because grub isn't showing Win 10 in the tab.

I've tried to re-install ubuntu with the grub boot selected to appear on the ubuntu disk but it didn't help - Windows 10 still wouldn't boot - instead grub would open in a rescue mode.

Normally I would re-formate the disk but I only have a digital license for my Windows 10 so I cannot aford the data loss.

Here is a Boot-Info pastebin with information: [http://paste.ubuntu.com/24020690/](http://paste.ubuntu.com/24020690/)

Can you please help me not to lose my Win license and make both operating systems boot properly?

Thanks in advance

---

### Post by oldfred on 2017-02-18
It looks like you booted Ubuntu live mode with Boot-Repair in UEFI boot mode, so you must have newer hardware.

But your drives are all MBR(msdos). Windows only boots in BIOS/legacy boot mode from MBR drives.

And it looks like Ubuntu also is installed in BIOS boot mode.

But Windows 8 or 10 has fast start up or always on hibernation. And the Linux NTFS driver will not mount read/write NTFS that is hibernated or if it needs chkdsk. And then grub cannot see nor boot the Windows install.
So you want to keep a Windows boot loader on the Windows drive. Windows will turn on fast start up on upgrades. So sometimes you may have to directly boot the Windows install to turn off Windows fast start.

Grub2's os-prober is not able to see that you have Windows if fast start up is on. So Boot Windows and turn off fast start up.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

It looks like you ran a Boot-Repair auto fix which installs grub to every MBR. Much better to use adanced mode and always choose an operating system and which drive toinstall its boot loader into.
You may be trapped into manually installing a Windows or Windows type boot loader manually either from Ubuntu live or Windows repair console from a Windows repair disk or installer. Boot-Repair (using NTFS driver) cannot see that you have Windows.
       
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

You also have SFS or dynamic partitions on sdc. Since you only show 3 partitions, not sure why it would have converted basic to SFS, as that is a Microsoft proprietary work around for the MBR 4 partition limit. Linux does not work with SFS, but they have been reverse engineering it and now may see that you have it. But still better not to have dynamic partitions. Even some Windows tools do not work with dynamic as you have to use the proprietary tools to manage those partitions.
[https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)

---

### Post by karlicka1 on 2017-02-19
Thanks for your support! I eventually managed to fix the Win 10 boot.

Instead of using bootrec I've had to manually use the command > bootsect /nt60 <drive letter>: /mbr for every partition of the SSD. When I used the SYS or ALL commands, it would not work.

---

### Post by oldrocker99 on 2017-02-19
Since you did solve your problem, please mark this thread as [SOLVED].

---

