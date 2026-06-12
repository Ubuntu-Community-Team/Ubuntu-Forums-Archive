---
title: "GRUB no longer boots to Windows after recreating the Windows partition"
date: 2014-08-10
forum: General Help
---

### Post by Jacob_Strandlien on 2014-08-10
I hope I'm posting this in the right place.  My weird complex problem is  (in short) that after recreating my Windows partition, everytime I try  to boot to Windows in GRUB, it blinks black for a second then goes back  to the GRUB screen.  Here's the full story.

I got a computer  preinstalled with Windows 8 and EFI.  I installed a second hard drive  and installed Ubuntu 14.04 on it, and was happily dual-booting for a couple  months.
Then the motherboard fried itself and I removed the Ubuntu  drive to send the rest into the manufacturer for warranty repair.  They  wiped and reimaged the Windows drive in the process of repairing it and  sent it back to me.
When I reinstalled the Ubuntu drive, it would  only boot into Windows and GRUB didn't show up at all (maybe I had installed GRUB onto the Windows  drive?  Not sure).  In any case, I used boot-repair-disk to reinstall  GRUB 2.02 and now Ubuntu boots flawlessly.
However, now GRUB does not  seem willing to properly boot into Windows.  When I select  "Windows Boot Manager", it flickers black for a moment and then goes  back to GRUB.  No error message.

update-grub has no effect on  this problem.  I cannot find any logs that give me useful information.   Can someone point me in the right direction?

Thanks!

---

### Post by ajgreeny on 2014-08-10
With your new Windows you may now have a secure boot problem, or any of the other myriad of UEFI problems that can occur.

Have you disabled secure boot, fast start etc etc in Windows, and are you sure that you have both OSs installed in the same UEFI/BIOS mode?

Show us the link that boot-repair makes which will give a lot more detailed info on which to work.

---

### Post by Jacob_Strandlien on 2014-08-10
Secure boot is off.  I turned fast boot off, but it didn't help.  Here's the link that boot-repair gave me:

[http://paste.ubuntu.com/8002866](http://paste.ubuntu.com/8002866)

---

### Post by oldfred on 2014-08-10
What brand & model?
You have this file in your efi partition.
 /EFI/Microsoft/Boot/bkpbootmgfw.efi

Which says you ran the "buggy" UEFI fix that Boot-Repair offers. After running that fix you can only boot Windows from the grub menu using this menu entry.     
menuentry "Windows UEFI recovery bkpbootmgfw.efi" {

Ubuntu's os-prober now finds correct Windows entry (it did not before and Boot-Repair fix was only alternative) but it is this filename, but with the rename it really is grub or shim and then it just loops back to grub menu.

 menuentry 'Windows Boot Manager (on /dev/sda2)'

But Windows updates may overwrite bootmgfw.efi which is really grub to then be a newer copy of the Windows boot loader file. Then you cannot boot grub and the bkpbootmfgfw.efi that was the old Windows efi boot file copy may not work.

From UEFI are you able to directly boot the Ubuntu entry 0000 or can you only boot Windows entry 0001 (which really then is grub?) If you can boot ubuntu entry then you do not need the rename.

      
 BootOrder: 0000,0001,2001,2002,2003
Boot0001* Windows Boot Manager
Boot0004* EFI USB Device (UFD 2.0 Silicon-Power64G)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR],BootCurrent: 0004

To be able to directly boot Windows from UEFI menu you can undo the rename with Boot-Repair.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by Jacob_Strandlien on 2014-08-11
Ouch!  That explaination may be a little over my head, but I'll take a stab at it.

I have a Lenovo Yoga 13 20175

If I'm understanding you correctly, you're suggesting that I may not need GRUB at all and that I may be able boot to Ubuntu directly from the UEFI menu.  Do you mean the boot-order menu at startup (F12 on my machine)?  If so, I already tried it, and it does not seem to recognize that my Ubuntu drive has a valid operating system.  And it is a serious pain to get into.  I have just a split second during startup to hit that F12 key, and it usually takes me two or three tries.  If there is any way to make GRUB work, I would much prefer that option.

I'll see if there are any other UEFI options that I'm missing, and try your "Restore EFI backups" solution.  But GRUB worked on my system before; couldn't it be made to work again?

---

### Post by oldfred on 2014-08-11
No, you need grub, but UEFI menu is a higher level boot menu and should always work.

I think you must have run the rename function with Boot-Repair before. That was pretty automatic as grub did not create a working Windows efi boot entry for several releases with UEFI.
There now are multiple other work arounds to get systems that do not boot ubuntu UEFI entry, not just the method that Boot-Repair did. That still should work but leads to issues after any Windows update as Boot-Repair method is renaming the Windows efi file.

Some other threads with Yoga
 Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

Work arounds.
       [http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by Jacob_Strandlien on 2014-08-13
Thank you Oldfred!  I still do not completely understand the explanation, but I ran the Restore EFI Backups and now it works!  Marking as solved.

---

