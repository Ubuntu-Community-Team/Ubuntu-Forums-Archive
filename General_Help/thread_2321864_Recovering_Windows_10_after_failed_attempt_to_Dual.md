---
title: "Recovering Windows 10 after failed attempt to Dual Boot."
date: 2016-04-25
forum: General Help
---

### Post by anbu3 on 2016-04-25
I tried to setup my computer to dual-boot in Ubuntu and Windows 10. I had to reinstall Ubuntu again because i hit my flash drive on accident during the first installion. So when I got to the options I clicked reinstall Ubuntu thinking that it would just replace Ubuntu, but after that I could not dual boot. I think that clicking on the reinstall option had the same affect as clicking on install Ubuntu along side windows 10, which I know you are not suppose to do.

I am looking for a solution to get back to windows 10 preferably with all my documents still intact. I don't have my recovery drive anymore since I had to delete it to make room for 2 additional partitions. I saw a early post where someone was able to upgrade from windows 8 to windows 10 by a media creation tool that was preinstalled. I went from windows 7 to 10 so I dont know if that is available to me.

I am currently error messages like:

Error mounting /dev/sda1 at /media/anbu/SYSTEM: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda1" "/media/anbu/SYSTEM"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Any help will be greatly appreciated.

---

### Post by HereInOz on 2016-04-25
Hello,

I think you might be in trouble, but there may be others who know more than I do in this area.  Firstly, I would take the disk out and see if you can put it in a USB cradle or similar, and access that Windows partition by plugging the USB cradle in to another Windows system.  If you can, then I would copy off all your documents on to another drive before you try anything else.  If you can't access that partition with the drive in a USB cradle, then you could be in for a tough day.

---

### Post by oldfred on 2016-04-25
You may not have lost partition at all, but did not turn off Windows fast start up which is always on hibernation. Windows is still slow booting, so they converted to hibernation whether you want it or not to make you think it boots faster.

But if an upgrade from Windows 7, you system is probably BIOS/MBR. And you have to boot into Windows to turn off hibernation. So you need your Windows repair flash drive and run fixMBR. You can also use Boot-Repair and in advanced mode choose to install a Windows type boot loader.
After fixing Windows, reinstall grub and after sudo update-grub should offer to boot either Ubuntu or Windows.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
      
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by anbu3 on 2016-04-25
Ok, I just installed the boot repair program. I don't see the option to install a windows boot logo in advanced options. Under the Grub location tab i do see an option to change to change the OS to boot by default to Windows(via sda4 menu). Also wonder if I do the recommended repairs would that fix my issue.

I included my boot summary if this helps. [http://paste2.org/0XYUaV6w](http://paste2.org/0XYUaV6w)

Thanks,

---

### Post by oldfred on 2016-04-25
It says default repair just reinstall grub to MBR.

Maybe because it cannot see the partition correctly, but I thought it still offered a default Windows type boot loader which is syslinux, the same boot loader used for the BIOS installer of Ubuntu.

This is in effect saying you left fast start/hibernation on:

```
The NTFS partition is in an unsafe state. Please resume and shutdown

 	Windows fully (no hibernation or fast restarting), or mount the volume
 	read-only with the 'ro' mount option.
 	mount /dev/sda1 : Error code 14
 	mount -r /dev/sda1 /mnt/boot-sav/sda1
 	The disk contains an unclean file system (0, 0).
 	Metadata kept in Windows cache, refused to mount.
```

---

### Post by anbu3 on 2016-04-25
Just to make sure I am with you, do I just click apply from here? 


[ATTACH=CONFIG]268629[/ATTACH]

---

### Post by anbu3 on 2016-04-25
[ATTACH=CONFIG]268637[/ATTACH]

Ok, I have two places where I can install Grub sda4 Im pretty sure this is my linux partition or sda which looks like it covers my whole harddrive.

---

### Post by oldfred on 2016-04-25
With BIOS you boot from MBR, not from a partition.

But you first need a Windows boot loader in MBR to fix Windows. Then you reinstall grub to MBR of sda, not to any partition like sda3.

I think this shows the screen you want or other ways to restore a Windows boot loader.
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

(Was first link in post #3)

---

### Post by anbu3 on 2016-04-26
Ok, and as of now should i exit out of the terminal and kill the current process eventhough I wont have GRUB and wait until i make a windows repair disk.
And I assume that if I do this and turnoff my computer I wont be able to run Ubuntu either. 

I keep making mistakes.

---

### Post by oldfred on 2016-04-26
Always best to have a bootable Windows repair flash drive and the Ubuntu live installer to use as a repair disk also. Then you have multiple ways to boot and repair system. 
Flash drives are now very inexpensive.

---

### Post by anbu3 on 2016-04-26
Would the steps shown on this website work for installing a windows boot loader without a disk.[ATTACH=CONFIG]268654[/ATTACH]

---

### Post by anbu3 on 2016-04-26
After I followed the steps in solution 2 that I found online, i was able to restore MBR using boot-repair. I was able to select windows 10 but got a blue screen saying I was missing a file and couldn't boot.
I thought I did not have to have to use a disk with windows on it according to this site.[ATTACH=CONFIG]268655[/ATTACH]:confused:

Is there any other options I have to change in boot repair before I run the repair or do i just really need a windows disk.

Wonder if you seen then method work before.

Thanks

---

### Post by oldfred on 2016-04-26
Boot-Repair can only do minor repairs.
But the repair it does to fix MBR for Windows is install syslinux.

Can you use the internal f8 just as Windows starts to get to its repair console. 
Otherwise you need a Windows repair flash drive or installer to use its repair console.
You can make a repair flash drive from another Windows computer that is same 64 bit (or 32 bit).  Do not think any Windows 10 are 32 bit, so any Windows 10 probably works to make repair disk.

---

### Post by anbu3 on 2016-04-27
Well since I don t have another windows computer can I'll just buy this windows easy recovery essentials for about $10.00

---

### Post by oldfred on 2016-04-27
If Windows 10 was pre-installed, it is UEFI and you should not be installing BIOS boot loaders as they will not work.

You may be able to press f10 or f12 (check manual for one time boot key) when starting system and choose Windows.

---

### Post by anbu3 on 2016-04-27
My Computer was originally on Windows 7 when I bought it so would it still not work

---

### Post by anbu3 on 2016-04-27
When I try holding the F10 or F12 while booting. I get a loud beep. Nothing appears on the screen but I do turn my computer off quickly(under 4secs)

---

### Post by oldfred on 2016-04-27
Shutdown while it may be writing data often causes corruption of file system.
Then you have to run chkdsk if NTFS or e2fsck if ext4 format before making other repairs.

If originally Windows 7 then probably BIOS with MBR partitioning. And then you do need Windows boot loader in MBR, and if you have the separate 100MB Windows boot partition, you can usually use f8 for its repair console as that is in the boot partition, not the main install.
Otherwise you do need the Windows repair flash drive.

---

### Post by anbu3 on 2016-04-28
F8 does nothing. it says im missing winload.exe in systems32 windows.

Any possible sites to download the files to make a recovery flash drive or do i need to get another PC to do it.

---

### Post by anbu3 on 2016-04-28
guess i could just by a flash drive

---

### Post by oldfred on 2016-04-28
If you have access to any other Windows 10 system, work, school, friend etc.

 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)

---

### Post by anbu3 on 2016-04-28
Is it possible for someone who has made a recover flash drive to put all the file in a folded and zip it and and send it to me by email and put the files on my flash drive.

---

### Post by anbu3 on 2016-04-28
maybe i should just by the cheapest PC to make a windows 10 recovery flash drive.

---

### Post by oldfred on 2016-04-28
We do not support violation of terms of service of other vendors.

But Microsoft offers a legal download (do not download from anywhere else) and I believe you have 30 days before you have to pay for it.

       Repair/backup/restore
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options
[/URL]
 Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO) 

[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

### Post by anbu3 on 2016-04-29
oh i didn't know using another persons recovery flash drive is a violation. But cant download anything really since im stuck on linux.

---

### Post by anbu3 on 2016-04-29
got the money to buy a laptop but my parents are going to question me why i have 2 laptops.

---

### Post by oldfred on 2016-04-29
Someone else's repair disk is not a violation. 

But downloading illegal copies of Windows is.

If Ubuntu is working, you can download the Windows file and install to a flash drive.

Some of the third party Windows vendors sell repair tools that may work. Cheaper than a new laptop.

---

