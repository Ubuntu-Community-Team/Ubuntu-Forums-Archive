---
title: "Install Ubuntu in Windows pre installed laptop (confusing partitions )"
date: 2015-02-07
forum: General Help
---

### Post by gopukrishnan on 2015-02-07
Hey Guys


I just bought a new lenovo laptop and it comes with windows. Before installing the Ubuntu, just had a check on the partitions and confused with the current partitions. In my old desktop, I used to install Windows first and then install the ubuntu with the freespace available. So ubuntu keeps the windows MBR along with the ubuntu. Here I can see some additional partitions named as EFI,OEM,Recovery etc.  Some recovery partitions are showing as 100% free. Can you guys tell me whether I can remove those or safe things to do before removing them ? I can install ubuntu in the freespace available but really frustrated to see those. I would have removed the windows OS unless I paid for it with the laptop.(Here in India most of the laptops comes with windows pre installed) I have attached the screenshots for better understanding.

[ATTACH=CONFIG]259792[/ATTACH][ATTACH=CONFIG]259793[/ATTACH]


Thanks,
Gopu

---

### Post by oldfred on 2015-02-07
That is the new standard UEFI with gpt partitioning. With gpt you do not have the limits on primary partitions.
But Windows implements secure boot option in UEFI.
System should have three ways to boot now. Before with BIOS you may have had to make one or two setting changes in BIOS to allow USB ports or other settings. With UEFI you often have to make many settings at least understand UEFI with secure boot, UEFI without secure boot and CSM or the old BIOS install. How you boot installer UEFI or CSM is how it installs and you only want UEFI, not CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You want to keep all the Windows partitions and must backup the Windows partition and the efi partition. Also  best to make the set of DVDs from the recovery partition. That probably only would be used if later you want to sell computer and want a clean Windows without your data.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

If looks like you have already shrunk the NTFS partition to make room for Ubuntu. Make sure Windows has updated itself to its new size and run chkdsk.
Make sure Windows 8 has its always on hibernation or fast boot turned off. And if UEFI has a separate fast boot setting turn that off also. UEFI (or BIOS) scan system for hardware on reboot and report that to operation system. Vast majority of cases hard ware has not changed, so a UEFI fast boot does not rescan system, but it can be so fast that you cannot get back into it to changesettings. Not sure if Lenovo has a setting, but my UEFI allowed a setting for full UEFI boot after power off, or full reboot and a delay setting on warm reboot, so I can get back into UEFI but still faster than the old BIOS.

Often better to turn off secure boot, but Ubuntu installer will install with secure boot on.

Some specific Lenovo issues, most issues are common across a Vendor's models. General UEFI info in link in my signature below.
Best to only use Something Else install option. Some current versions of Ubuntu have a major bug that erases entire hard drive with the auto install option if Windows is not seen or on reinstall.

      
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not any other entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

---

