---
title: "Windows 8 partition won't boot.  EasyBCD hosed it."
date: 2014-05-18
forum: General Help
---

### Post by jspencerseiler on 2014-05-18
Greetings, 

This will be a longish explanation so please bear with me.  My actual desire was to upgrade my 13.04 Ubuntu partition to 14.04 LTS.  However I could not get my laptop to boot from the USB drive.  I have an ASUS K55A.  I have been happily in 13.04 since it came out and I am dual booted because I need the windows partition for work.  The machine use uefi.  Which I honestly hate.  I have never been able to upgrade this machine without uefi issues.  Anyway I was attempting to boot from the USB from the windows partition and it wouldn't recognize it.  I had disabled fast boot and secure boot and tried to get the firmware to look at the usb first but I was luckless.  So I got it into my head that easyBCD might fix it.  Bad idea.  Now I cannot boot windows at all and I get the 'use your installation disks to do a repair' screen.  Fortunately I can still boot into Ubuntu, I tried executing Boot Repair but that was no go either.  My Boot Repair log output is here.  [http://paste.ubuntu.com/7484739](http://paste.ubuntu.com/7484739) 

All I really wanted was to upgrade my 13.04 to 14.  But it would't do it and then I chased the rabbit down this hole.  So the first thing I would like to cure is getting my windows partition to boot.  The partition is there and the files are there because I can mount it from Ubuntu but I hosed the boot record or something.  Can anyone help or has anyone had this type of issue happen to them?  Any assistance is greatly greatly appreciated.  

thanks!

---

### Post by oldfred on 2014-05-18
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

You ran the 'buggy' UEFI rename. Did you do that before or just now? 
This is the original Windows boot file, but with rename only grub entry can boot it.

 /EFI/Microsoft/Boot[COLOR=#ff0000]/bkp[/COLOR]bootmgfw.efi 

If you undo the rename then you should be able to boot Windows directly from UEFI menu. With the rename, booting the Windows entry actually boots grub. That is for those UEFI where vendor modified UEFI to only boot Windows.

 Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

If you boot Ubuntu entry from UEFI can you boot Ubuntu? Or do you have one of the problem UEFI systems?

You probably need to directly install 14.04 over your obsolete install. But see caution in link in my signature.

---

### Post by jspencerseiler on 2014-05-19
Thanks for your reply!  I noticed the 'buggy' thing when I ran boot-repair.  This is the first time I recall seeing it as I didn't see it in my previous upgrade.  (12 to 13)  and I did reply yes or rather I took the default which was yes.  I have not ever tried to boot Ubuntu from UEFI I don't believe.  But I may misunderstand your question.  I have always booted Ubuntu or windows from the GNU Grub menu that is the first thing that comes up on a reboot.  And I have it set to default to Ubuntu as that is my preferred OS. 

I tried also altering GRUB to point to the bootx64.efi rather than the bkpbootx64.efi and that simply caused the screen to blank out and then return to the GRUB menu.  I will rename them back and update grub.  I will rerun boot repair with the restore option.   Likely this will happen this evening and I will report my results later tonight.   

Will installing 14.04 directly over my 13.04 cause me to lose all my 'stuff'?  When I attempted a 12 to 13 upgrade it went south and I had to install 13.04 'fresh'.  At one point it the install detected that a Ubuntu system was installed and there was an option to keep my settings but I lost that when I had my problems with that upgrade.  Will 14 do the same thing?  Or will it be a fresh, laid in new install wiping out all my previous settings/stuff?  

Thanks very very much for the help.  I will report back with results tonight.  After I review the UEFI thread and rerun boot-repair.

---

### Post by oldfred on 2014-05-19
If you tick the format button it overwrites everything. Some do what is called a 'dirty' install and only new stuff is overwritten but that may include custom settings and other things. Best to have a full backup of /home, perhaps /etc and a list of installed applications to make it easy to reinstall all the apps  you added.

While you can backup /home from a live installer, you cannot easily extract a list of installed apps unless you can boot or chroot into old install.
       Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
      [/URL]
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

    [       ]("http://ubuntuforums.org/showthread.php?t=1748541")
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

    [URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

### Post by jspencerseiler on 2014-05-19
Alas, no success.  I reran the boot-repair and it ran successfully.  log is here; [http://paste.ubuntu.com/7490590](http://paste.ubuntu.com/7490590) .  However I think I hosed my win 8 before I tried boot-repair and I am not sure how to fix it using any method at this point.  When I select the windows option from the grub menu, it goes directly to this screen that says your partition has a problem and use can use your install disks to fix it.   It shows  a \BCD followed by a 0xc0000098 then the info says: the boot configuration file doesn't contain valid information for an operating system.  It's kind of a scary message.  Fortunately for me Ubuntu boots up nicely and that's where I spend most of my time.  There is nothing on the windows side I would care if I lost.  That being said I do use it for work in order to connect to the network there.  So I am thinking that whatever I did with easyBCD messed it up.  I don't know what I did, sorry.  I am hoping that easyBCD backed up the old BCD and all I need to do it replace the new one with that.  I am just kind of lost with this now.  I will keep poking at it but if you have and good ideas or simply know how to fix this I would be very appreciative.  Thanks!

---

### Post by oldfred on 2014-05-19
Grub has not booted Windows from grub menu until os-prober was fixed with 13.10. The  os-prober only created BIOS boot entries which do not work with UEFI. New versions all are fixed, yours is not.

You still should be able to boot Windows from UEFI menu.
The entries in 25_custom added by Boot-Repair also should work if Windows was left in a working state. 
But if it needs chkdsk or is hibernated you may have to boot from UEFI and use f8 to get into repair console. Or you need to have a Windows repair flash drive.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by jspencerseiler on 2014-05-19
Sorry to display my ignorance, but when you say boot from UEFI are you referring the the first menu that comes up on boot?  Or is there another ?  I guess I am confused.  What I am calling grub may not be correct.

---

### Post by jspencerseiler on 2014-05-19
Wait I think I know what you may mean!  The UEFI you are referring to would be what at one time was the BIOS screen?  Under the save and exit tab there are boot options.  If I select Ubuntu it goes to what I have been calling the grub screen and boots Ubuntu.  If I select the windows boot manager then it gives me a partition error invalid partition and goes to grub rescue.  I think I need to rebuild my BCD on my windows partition.  Is there a way to do that from Ubuntu?  Or do I need to create a windows recovery disk?

---

### Post by oldfred on 2014-05-19
You have to use Windows repair tools to fix a BCD. Some of the third party Windows tools may also help.
It may need chkdsk or fastboot turned off?

---

### Post by jspencerseiler on 2014-05-19
Thanks.  I will see what I can dig up and post my results back here.  It may be a few days.  Stay tuned.  Thanks for all your help.

---

### Post by oldfred on 2014-05-19
Several UEFI menus.

---

### Post by jspencerseiler on 2014-05-25
Looks like I am in business.  My windows partition will now boot.  My BCD did indeed need to be rebuilt and once that was done I was all set.  Thanks for your help and advice.

---

