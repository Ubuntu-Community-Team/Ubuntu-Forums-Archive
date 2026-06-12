---
title: "I ruined my mum's PC"
date: 2018-03-28
forum: General Help
---

### Post by singsing123 on 2018-03-28
Hello, 

I tried to dual boot Ubuntu 16 LTS alongside Win 10 Pro but now Windows 10 won't work. When I try to load Win 10, it just goes to the blue repair screen. When I try to repair, it fails. When I try to restore an earlier version, it fails. So I tried to access my mum's important files via Ubuntu, but I get this message: 

Error mounting /dev/sda2 at /media/ubuntu4dmin/DABE2832BE280999: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda2" "/media/ubuntu4dmin/DABE2832BE280999"' exited with non-zero exit status 18: Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda2': No such file or directory

How can I fix this? My mums files are the most important, not Windows 10. However, If I am able to get Win 10 and the files, that's better.

---

### Post by Irihapeti on 2018-03-28
*Moved to **General Help** for a better fit.*

---

### Post by singsing123 on 2018-03-28
Thanks. 

And I totally agree with your signature "*Please, people, remember to _**[BACKUP]("https://help.ubuntu.com/community/BackupYourSystem")**_ before you install that new system. Same if you're upgrading. *

---

### Post by yancek on 2018-03-28
The message you posted doesn't look good for recovering files or windows.  Best to see details.  You don't indicate whether you can boot the installed Ubuntu??  If you can use that, otherwise use the Ubuntu install DVD/usb and go to the site below and download and run boot repair according to the instructions on the page.  Make sure you do NOT try any repairs but rather, select the Create BootInfo Summary option and when it finishes, post a link to the output here.  That should provide some details on the computer and enable someone to suggest possible methods to recover.  On boot repair, use the 2nd option to install it.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2018-03-29
As long as we haven't ruled out the possibility that the Windows partition with the documents was overwritten by your Ubuntu install, it's better to use the install disk anyway. The less writes to your harddrive, the better, in case you may need file recovery. So don't use the installed Ubuntu system.

---

### Post by deanr2 on 2018-03-29
I had a similar issue with a dual boot. 

I created a Windows 10 DVD-ROM and booted from that. At some stage it gave the option to install Windows and keep files in tact so I managed to salvage Windows 10 in the condition in which I had left it. Try that.

---

### Post by Mark Phelps on 2018-03-29
Win10 AUTOMATICALLY goes into Hibernation when it is not running, and this keeps the windows filesystem volumes MOUNTED -- which then presents Linux from mounting them.  The fix is to go into Win10 and DISABLE Fast Startup (NOT Fast Boot -- something different), but since you can't get into Windows now, that is going to be very difficult to do.

You would need access to another, working, Windows PC so you can remove the drive from this PC, connect it to that PC (using a USB-to-Hard-Drive adapter), and see if you can recover any of the files and folders.

That would be my preferred approach at this point -- doing file recovery.

---

### Post by mastablasta on 2018-03-29
> **Mark Phelps said:**
>  The fix is to go into Win10 and DISABLE Fast Startup (NOT Fast Boot -- something different), but since you can't get into Windows now, that is going to be very difficult to do.
.

couldn't they just reinstall the windows boot loader, boot into windows, fix the issue, then reinstall the GRUB (Linux boot loader) ?

---

### Post by oldfred on 2018-03-29
+1 on mastablasta's suggestion if BIOS.
If UEFI, you just need to directly boot from UEFI boot menu.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by singsing123 on 2018-03-29
@everyone,

Thanks for the support. The issue is still not fixed though.

@mark phelps,

That was my initial thought.

@oldfred,

bootrec.exe /fastboot doesn't work for me. I tried this (watch?v=rczKC7w302U) tutorial but it still didn't work. Error message: The file or directory is corrupted and unreadable. 
bootrec.exe /fixmbr worked.

I installed Windows 10 in Ubuntu's place now (dual-booting Windows 10/Windows10). I tried to access the directory (my mum's computer) from the new Windows 10 (Ubuntu replacement), but I get this message: E:\ is not accessible. The file or directory is corrupted and unreadable.

I have definitely NOT formatted or installed Ubuntu/Windows on the original partition (120gb ssd). All installations have been performed on a different 13~GB partition. How should I approach this?

---

### Post by singsing123 on 2018-03-29
Update: I tried to chkdsk /f e: on the original Windows 10  in cmd via blue repair screen. It processed the request and said "Windows has scanned the file system and found no problems. No further action is required." It also recognized e: as NTFS. 

When I tried to chkdsk /f e: in CMD via the new Windows normally, it said "Stage 1: Examining basic file system structure . . .  . . Corrupt master file table. CHKDSK aborted. "

---

### Post by SeijiSensei on 2018-03-29
Take a look at [photorec]("https://www.cgsecurity.org/wiki/PhotoRec"). It's pretty highly regarded as a tool for restoring files.

---

### Post by yancek on 2018-03-29
> When I tried to chkdsk /f e: in CMD via the new Windows normally, it  said "Stage 1: Examining basic file system structure . . .  . . Corrupt  master file table. CHKDSK aborted. " 				

I think it is well past time to head to the support.microsoft forum or some other windows forum.  You haven't posted any details on drives partitions as requested earlier so everyone here is guessing.  If you boot into a windows system, it will show itself as being on the C:\ drive.  If you boot into another windows system on the same computer, it will also show itself as the C:\ drive so when you ran the successful checkdsk from the old windows, you were actually running it on the partition of the new windows which is why you got no errors.  Your system is corrupt for some unknown reason.  We don't have any details on what happened except that an attempted install of Ubuntu was done incorrectly and failed for some reason.

---

