---
title: "Lost ablity to boot windows 8 in dual boot system with ubuntu 12.04"
date: 2014-07-16
forum: General Help
---

### Post by mwk29162 on 2014-07-16
I have a dual boot system Ubuntu 12.04 and windows 8 and somehow when tying to update Ubuntu the grub was rewritten and I lost the ability to boot into windows 8. I tried boot repair and I got this output file but it didn't repair anything. Could someone please take a look at this output file and see if you can figure out what I need to do to fix this? Thank you so much!

                                                                      [http://paste.ubuntu.com/7803733](http://paste.ubuntu.com/7803733)

---

### Post by P_THE_AWESOME on 2014-07-16
Welcome to the Ubuntu Forums!

You chose:
> This setting will reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
So you need to boot into [FONT=courier new]sdb[/FONT] from your BIOS.

It also says at the bottom of that file:
> You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (500GB) disk!
More proof. Set the Boot Order in your BIOS options. You seem to have two hard disks.

Good luck and enjoy Ubuntu!

---

### Post by oldfred on 2014-07-16
Even though Windows 8 is in BIOS boot with MBR partitioning you have to have fast boot or always on hibernation off if you want to boot from grub menu.

You should reinstall Windows boot loader to sda, so you can directly boot from BIOS or one time boot key, often f12 but varies by vendor.
Boot-Repair's default is just to install grub to every MBR, but you can use advanced mode and choose Windows and choose sda to reinstall a Windows boot loader.

OR use your Windows 8 repair flash drive to fix Windows. Should be similar even if not UEFI.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
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

---

