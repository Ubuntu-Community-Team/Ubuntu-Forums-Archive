---
title: "Multiple problems with booting"
date: 2014-08-02
forum: General Help
---

### Post by sylvester2 on 2014-08-02
**Hello Ubuntu users. **
I have a quite problem and I am out of ideas how to fix it, my last option was to ask for help in forums, so here I am.

I am in a situation where I can't boot into Windows or Ubuntu, so I will tell you how everything went.

Decided to try Linux, so I looked up multiple Distributions and I personally really liked Elementary OS, so I installed it along with Windows  which I was using at the time, installed it using USB drive. I have **2 hard drives**. Have mine Windows in one hard drive (160gb) and installed ElementaryOS on other one (1tb). I was using both OS and I was able to boot in both. Then I decided to install pure Ubuntu, because I needed newer version of Ubuntu ( ElementaryOS is based on Ubuntu 12.04 ). So I made a bootable USB with Ubuntu inside, I booted it up and in installation I choosed "Something else" in installation type menu, there were 2 hard drives, one was that 160gb hard drive which had 1 partition that only contained windows, and there was my 1tb hard drive which contained multiple partitions - "Windows bootloader" (or something like that), root, swap and home partitions. I deleted them all **INCLUDING Windows bootloader** because I thought that windows is still going to be bootable as Windows is in seperate hard drive. I made exactly the same partitions for Ubuntu - root, swap and home. Installation went well, I rebooted my PC after installation and it booted straight into Ubuntu and there I faced my first problem, in** login screen I got a notification that I have been disconneted from network and after the notification disappeared, everything froze up**, I couldn't even open terminal with CTRL+ALT+F1, I restarted my PC and nothing change unfortunately, so I decided to boot in Windows, but **in GRUB bootloader there was no Windows** and if I boot in Ubuntu, everything freezes up, so I can't boot in any OS. I tried to reinstall ubuntu through USB again using "Replace Ubuntu with Ubuntu" in installation menu, everything reinstalled fine, but I still had that problem with freezing up. After that I searched for solutions in Live USB Ubuntu, tried Boot-Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), but there still was no Windows in GRUB bootloader. Also I have no Windows CD/USB installation with me, only this USB which contains this Ubuntu I am now using in Live Try. I am thing maybe I can fix that freezing up problem so I have atleast 1 usable OS. 
[B]
tl;dr[/B]
I have 2 hard drives, 1 hard drive contains Windows, other one contains Ubuntu which is unusable (freezes up or input not working), tried reintalling Ubuntu, didnt help. Can't boot into Windows because GRUB bootloader doesn't show Windows there (because I deleted it).

Also, I have keyboard that works like a PS2 keyboard, so keyboard itself probably isn't the problem.

I'm really desperate, please help. Thanks.

[B]
EDIT:[/B]
Remebered that I also saved the boot-repairs log about my computer.
[http://paste.ubuntu.com/7933155](http://paste.ubuntu.com/7933155)

Also I can see all my Windows files are still there unharmed or anything. I can access them for Live Ubuntu in File explorer going to that 160gb hard drive. If I could only put some missing file or something in that hard drive that will make it bootable?

---

### Post by oldfred on 2014-08-02
Windows 7 &  8 have a separate 100MB boot partition which you do not see from Windows. It is installed on the drive that you have set as bootable in BIOS. So if you install Windows on a second drive but have first drive set as boot the boot partition for Windows is on the other drive.

You really need a Windows repair disk CD or flash drive to fix the issue. You can set BIOS to boot from Windows drive and make sure boot flag is on the main Windows install.
But you are missing these first two boot files.
 Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Did you run Boot-Repair before deleting the Windows boot partition? It probably made a backup. Or did you back it up otherwise?
You can look in your main install and see if it has a backup somewhere in system. Or if you have access to another system with Windows 7 make a repair flash drive.
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)
      BootRec.exe /RebuildBcd

      Some third party tools may be able to recreate the BCD.
 [URL="http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"]http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD
[/URL]
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

With two drives do not use Boot-Repairs auto fix as that just installs grub to both drives. You want the Windows boot loader in sdb or the 160GB drive. The advanced options of Boot-Repair or Windows tools will reinstall a Windows boot loader. Just make sure BIOS is set to boot 160GB drive first when making repairs.

Once you get Windows working we can see what the grub issues are.


[URL="http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"]
[/URL]

---

