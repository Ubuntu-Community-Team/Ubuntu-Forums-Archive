---
title: "Windows Does not Boot"
date: 2014-04-28
forum: General Help
---

### Post by harimkwon on 2014-04-28
I installed Grub into the sda1 Windows partition and when I restarted my computer, an error showed up at boot. So I reinstalled Ubuntu and installed Grub into sda1. Now I was able to get to the Grub menu. When I tried to boot into Windows Vista, Grub would just reboot. So I have tried /rebuildbcd /fixmbr and /fixboot. I tried reinstalling Vista as well. Now when I boot into Vista, I get a blinking cursor and a black screen. Does anyone have a solution to this problem? Thank you.

---

### Post by oldfred on 2014-04-28
You cannot install grub to any NTFS partition's boot sector. That has to have Windows boot code. And if you really have grub in the PBR, Windows will not even let you fix it as it does not see a NTFS partition.

Post link to BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Check to see if this issue:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by harimkwon on 2014-04-29
I burnt a boot repair iso onto a cd and clicked 'create bootinfo."
This is what I got: 
[http://paste.ubuntu.com/7357015/](http://paste.ubuntu.com/7357015/)

I could now start boot repair in Ubuntu, I was a little confused earlier.

Thank you for your help.

---

### Post by harimkwon on 2014-04-29
Testdisk said that my boot sector was good and backup boot sector okay. So I pressed BackupBS and restarted but Vista would not load but showed up on the Grub menu. Then I went back into Ubuntu and used Boot-Repair. I clicked on advanced/other options/Repair Windows Files. That still did not work. So I put in the Vista installation disk and tried "bootrec.exe /fixboot" and "bootrec.exe /fixmbr." Now Grub does not load and I get a flashing cursor at startup. Is there anything I may have done wrong or anything else I could do? I did these steps earlier and this is my second time trying them. When I got the flashing cursor at startup earlier, I reinstalled Ubuntu and installed Grub into Sda. Windows would still not load. So I came to the forums. The reason why I installed Grub into the Windows partition earlier was because I read a post from another user saying that Grub needs to be installed into /Sda1 (with windows partition). 
Here is the Bootrepair info:

[URL="http://paste.ubuntu.com/7357222/"]http://paste.ubuntu.com/7357222/


[/URL]Edit: I used boot repair to repair the grub bootloader and can not boot into Ubuntu but still not vista. I have another Vista laptop. Could I just copy the system files from that laptop into the one that won't boot Vista?

After running the Bootrepair Info again, I got [http://paste.ubuntu.com/7357237/](http://paste.ubuntu.com/7357237/)

---

### Post by oldfred on 2014-04-29
You are showing a Windows install in sda5. And it shows a NTFS PBR partition boot sector issue with start sector.

```
  Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 184647680.


```

Windows will not directly boot from a logical partition like sda5, and it only boots from a primary NTFS partition with the boot flag. Your sda1 has boot flag and boot files for XP and newer bootmgr & BCD to boot Vista or newer systems.

Now sure exactly how to repair a Windows install in a logical partition. You still should be able to run chkdsk on it from a Windows repairCD or flash drive. Not sure if you can get into repair console with f8 with Vista.
But grub boots so quit you cannot use f8 on Windows boot entry in grub and would have to run the fixMBR command to directly boot Windows again. And then after fixing Windows restore grub boot loader to MBR.

Better to always have Windows in primary partitions. Ubuntu works just fine from logical partitions so reserve primary partitions for Windows.

---

### Post by harimkwon on 2014-04-29
I have Vista in 2 partitions. One is in sda1, which is 90gb and the other is in sda5, which is 9gb. After I tried all the solutions I've heard of, I decided to reinstall Vista on another partition so that I would not lose my drivers or Word 2007 (I don't have the product key). I thought the installation would reinstall the bootloader. Should I remove my second install of Vista? The recovery partition in sda3 works fine and I can use it to access system repair.

I might also add that when I first installed Ubuntu and rebooted, I did not get to any bootloader, so I reinstalled Ubuntu so I had it on another partition. When I installed Vista again, I deleted the second Ubuntu install and placed Vista in it.
Thank you for your help, it appears that I screwed up my computer. :(
But its not too bad since I can use Ubuntu.

So I tried bootec.exe /fixmbr and now I get the flashing cursor after the bios.
So I will place the Boot-Repair disk back in to reinstalled Grub.

---

### Post by oldfred on 2014-04-29
Your sda1 only shows XP boot files and two of the main Windows boot files. bootmgr & BCD
It does not have this:
/Windows/System32/winload.exe

With Windows 7 you normally have the two boot files in a separate Boot partition adn winload in the main install.

But with Vista they normally are in same partition.
Are you sure you were not booting from sda1 but install was sda5?

---

### Post by harimkwon on 2014-04-29
I'm sure. The computer came with Vista preinstalled and I installed Ubuntu next to it. I used Disk Management to make some partitions. After installing Ubuntu, I couldn't get Vista to boot, so I installed another copy of Vista into sda5. That copy of Vista in sda5 does not show up in Grub. I do have another computer with Vista. Could I copy Winload.exe from it and place it into the pc that doesn't boot Vista?

---

### Post by oldfred on 2014-04-29
You can usually copy bootmgr and BCD, but BCD usually then needs repairs to have correct info.

But winload.exe is in the main install.
 So did BootInfo just not show file & systems folder for your Vista and file is there. 
Otherwise it looks like it is not an install.

---

### Post by harimkwon on 2014-04-29
So I deleted winload.exe from system32 (but I saved a copy in another file). I emptied it from the trashcan in Ubuntu and I tried running startup repair, but it did not detect a problem. So I ran the command prompt from the Vista installation disk and typed in sfc /scannow. It could not start the repair service. I thought if I got the installation disk to place winload.exe back into system32, the computer might recognize it as a boot file. Is there any other way to run sfc /scannow? Or is sfc /scannow useful for my problem? I notice that my boot files are 
/boot.ini /bootmgr /boot/BCD /ntldr /NTDETECT.COM

And I am missing Winload.exe. This was happening even before I removed Winload.exe. It appears that Winload.exe is recognized in sda5.

And how come the second installation of Vista doesn't show up in Grub?

I can't run chkdsk from the Vista installation disk because the volume is write protected.

---

### Post by oldfred on 2014-04-29
Windows only has boot files in one active partition or the one with the boot flag. And only the active partition on the drive set to boot from in BIOS.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

But you can only get Windows to directly boot from a primary NTFS partition, not a logical. Linux works from Logical partitions.
Grub only finds a Windows partition with boot files ntldr & boot.ini for XP or bootmgr and BCD for all newer versions.
      
 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by newbie2244 on 2014-04-30
I have Windows8 on my system. I also had some problems but eventually succeeded in spite of myself. QUESTION: After you installed Ubuntu, and rebooted, what was the "error" that occurred?

 Below, is what I posted about my install in March. It's not well-written but it beats having to rewrite it.  After you read it if you have any questions, pls post questions and I'll reply. My original problem was that I wanted more than 30GB 
for my Linux install.  So I made some large  partitions. I am not sure if this applies to your system as you have Windows XP? 
_________________________________________________________________________________________________________________________________________________________________________________
 
  
" I have an HP Pavilion with Insyde? BIOS which came with WIndows 8. Be patient with my description because I don't fully understand this myself. ----- I made a bootable USB stick with Ubuntu Linux 12.04LTS. ___ In BIOS, I enabled virtualization first. [YOU MAY NOT NEED TO THIS].   Then in BIOS, I changed the boot order so that the USB drive was first. USB loaded and Linux finally loaded (a kind of temporary mount). But I couldn't install it to HD. I was connected to the net. I did a boot repair within the loaded Linux. And then ran the installer (universal installer). Still couldn't get an Ubuntu install on HD. Disabled secure boot. Same problem. Enabled Legacy Support. Ran the installer -- and finally got Ubuntu installed on the HD. Shutdown and started. Disconnected the USB stick and booted directly into Linux. OK but I needed dual boot. Went back to BIOS and changed boot order again so that the first boot device would be OS Boot Mgr. Shutdown (not restart). Started and got GRUB menu. --Very long listing.  . In order to boot Windows, I had to select a file named Windows UEFI bkpbootmgfw.efi, about halfway down the menu listing. ANd now Windows appears 2B embedded in Ubuntu with 207 GB of disk space.

---

### Post by drink1297 on 2014-04-30
Your issue is Linux installs first, THEN windows (and on an NTFS partition)....if you can, I would DBAN the eniter disk, reinstall Linux, then install Windows

---

