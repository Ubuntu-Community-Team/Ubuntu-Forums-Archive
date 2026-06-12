---
title: "Uninstalling Ubuntu"
date: 2013-11-18
forum: General Help
---

### Post by gunmasta99 on 2013-11-18
Hey everyone,

I messed up.

I was trying to uninstall Ubuntu from my computer and move back to Windows 8, but it didn't go over so well. I went into my Windows 8 installation, deleted all the Ubuntu hard drives by using the Disk Management Utility, and then went into PC Settings, General, "Reset Windows," as I figured this would be the best way to go about getting the EFI (I think that's what it's called, whatever is replaced by GRUB) back.

It didn't work, and now when my computer boots up, I don't even see my bios splash screen before I am greeted with the lovely terminal saying, "error: no such partition. grub rescue> "

What do?

---

### Post by david98 on 2013-11-18
I have not used window's for a while but i assume grub removed window's boot manager best way to repair it would be to put window's 8 disk in and click the repair option assuming you have a window's disk if not there are many well known torrent site's you could get one from.

---

### Post by gunmasta99 on 2013-11-18
Yeah, exactly. Grub did remove the boot manager. I don't have a Windows 8 Disk, and I currently reside at a Public School in the United States, so my internet connection is immediately shut down any time I download anything via any kind of peer-to-peer connection.

Is there anything I can do from inside the grub rescue menu?

---

### Post by oldfred on 2013-11-19
If you installed both Ubuntu & Windows in UEFI mode, you should just go into UEFI/BIOS menu and change to Windows efi entry.
If you install Ubuntu in BIOS mode, you just need to change from BIOS/CSM/Legacy boot to UEFI boot and choose Windows.
If you ran Boot-Repair and it renamed efi files you need to change names back. 

If you uninstalled Ubuntu you may not be able to boot from grub rescue.
If both are UEFI, you may be able to do this.

         search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi

But BIOS and UEFI are not compatible, so if you have started to boot grub in BIOS mode there is no way to switch to UEFI mode and boot Windows. You then have to boot Windows from UEFI menu. You may also have a one time boot key?

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by gunmasta99 on 2013-11-19
I installed Ubuntu via a flash drive onto my laptop.

I have already deleted all of the partitions that Ubuntu had anything to do with, and it's only down to the initial four that Windows 8 is using.

I can not access my BIOS any more, because the only thing that happens when I boot up is the grub rescue terminal shows up.

I will have to try that command as soon as I can.

I don't know if grub was booting in BIOS mode or UEFI.

I don't know what a one time boot key is, so I'll take a look at the link you posted.

Thank you.

EDIT:

I can go to the library on my school's Campus and purchase a Windows 8 Upgrade Disk for $10, would I be able to boot from this disk and restore the EFI boot loader?

EDIT2:

I used the Boot Key that was mentioned for Asus PC's in that link you posted (delete key); and it worked! Woohoo! I deleted the Ubuntu boot options in my BIOS menu and set the Windows Boot Manager to the default boot option. My PC is being reset right now.

Thanks a lot!

---

### Post by oldfred on 2013-11-19
Glad you got it working.
If you can get a full install ISO for $10, it may be worth havingm, if just an upgrade for older Windows maybe not. But then make your own repairCD.

Also backups and a repairCD are worth having also but you can do those all yourself.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Ralph_Lam on 2014-01-25
related topic - what if I want to install another distro in the same partition that I had installed Ubuntu on.  I am sure that it will pause to remind me that everything on the partition will be erased.  Will grub be updated and still boot from Windows, the other distro partition and the new new distro I put on the what was the Ubuntu partition?

---

### Post by deadflowr on 2014-01-25
> **Ralph_Lam said:**
> related topic - what if I want to install another distro in the same partition that I had installed Ubuntu on.  I am sure that it will pause to remind me that everything on the partition will be erased.  Will grub be updated and still boot from Windows, the other distro partition and the new new distro I put on the what was the Ubuntu partition?

You'll be installing whatever boot program the new system would be using.
So, it'll depend on that.
Most likely the grub you have will be overwritten.

---

### Post by oldfred on 2014-01-26
With new hard drive's being very large, it is possible to install several other operating systems to try out if desired. Just allocate another 20 or 25GB for a new / (root) partition. The main issue is keeping track of which install's boot loader is the one you are booting with.

With UEFI every install puts its boot loader into the efi partition and you can choose from UEFI menu which to boot. With BIOS there is only one MBR per hard drive, so each install is in charge.

And with UEFI deleting Ubuntu will not delete Ubuntu folder in efi partition nor ubuntu entry in UEFI NVRAM. You have to manually delete those.

---

