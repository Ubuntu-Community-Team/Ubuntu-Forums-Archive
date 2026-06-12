---
title: "Unable to access Windows 10 after installing Ubuntu 16.4"
date: 2016-10-13
forum: General Help
---

### Post by Myles_Vance on 2016-10-13
So I partitioned my hard drive to install Ubuntu 16.4 alongside Windows 10, and now I am unable to boot into Windows. It shows a blue screen telling me that there's been an issue, and that restarting might help. It doesn't help, and I've tried to reset Windows back to factory defaults and it fails. 

I've also run Boot Repair and it changed the name of Windows on the GRUB menu but it hasn't done much else, I'm lost as to what I should try next. 

It's a Toshiba Satellite, and it originally came with Windows 8. I've had Ubuntu on it before alongside Windows 8 with no problem, and I went back to just Windows a year or so ago. Now I decided to add Ubuntu again and now I'm having the problems.

---

### Post by leunam12 on 2016-10-13
Have you checked the HDD for errors?

---

### Post by Myles_Vance on 2016-10-14
How should I go about doing that? 
Sorry, I've been using Ubuntu on and off for years but I really should be considered a beginner when it comes to things like that.

---

### Post by leunam12 on 2016-10-14
Open the "Disks" utility and then go to menu and check the SMART data and self-test. See if there are bad sectors or reallocated sectors.

---

### Post by Jimysbil on 2016-10-14
It could be a problem to your NTFS filesystem (or at least a problem for windows).Can you mount your Windows partition from ubuntu or is that giving you some error??
In case your filesystem is damaged you can fix it by using a Windows 10 DVD/USB and run a chkdsk from there.
What is the error code your Windows blue screen appears??

---

### Post by Myles_Vance on 2016-10-14
When I try to mount my Windows partition from Ubuntu it gives this very long error:

"Error mounting /dev/sda2 at /media/myles/A6DAAAF4DAAAC043: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda2" "/media/myles/A6DAAAF4DAAAC043"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
 (udisks-error-quark, 0)"

Disk utility states that the disk is OK.


Windows no longer shows an error code, now when I try to boot Windows it just shows a black screen for a bit and then returns to the Grub. When I try to boot it a second time it shows the blue screen that tells me Windows has a problem starting and that restarting may fix it. It also offers a link to troubleshoot it, but none of the options under the troubleshooting link work. 

The blue screen with an error code stopped showing up after I ran Boot Repair.

---

### Post by Myles_Vance on 2016-10-14
It may be worth noting that Windows shows up twice in the GRUB. "Windows 10 (Loader) (on /dev/sda1)" and "Windows 10 (Loader) (on /dev/sda2)"

---

### Post by Myles_Vance on 2016-10-14
Okay, I'm able to access a command prompt through Windows. Chkdsk does find problems, and when I try to run chkdsk/f it says 
"The type of file system is NTFS. 
Cannot lock current drive. 
Windows cannot run disk checking on this volume because it is write protected."

---

### Post by yancek on 2016-10-14
You mention 'boot repair' in two of your posts but you haven't posted a link to the output it creates so there isn't much to go on.  The error you get with the mount command is a result of the windows system not being  fully shut down but rather being hibernated.  That is the default for newer windows versions and no Linux system will mount a hibernated windows partition.  Post the link to the boot repair output.

---

### Post by Myles_Vance on 2016-10-14
Here's the link from Boot Repair, sorry about neglecting to post it before. [http://paste2.org/Np1VaxHE](http://paste2.org/Np1VaxHE)

---

### Post by oldfred on 2016-10-14
You have BIOS/MBR installs.
If you did not turn off the fast start up in Windows, you will have to temporarily reinstall the Windows boot loader, boot Windows, turn off fast start up and use Boot-Repair to reinstall grub to MBR to dual boot.

You may be able to get Boot-Repair to install the syslinux boot loader in advanced options to MBR, but if it does not see Windows it may not offer that choice.
Best to use your Windows 10 repair/recovery disk to run fixMBR command.
You may be able to use Ubuntu installer to manually install syslinux or lilo boot loaders to MBR. You only want MBR, not full boot loader as that may corrupt Windows.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Shows install of Lilo boot loader to MBR.
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Lilo may complain about not fully installed, but that is what you want, just MBR boot loader.
or:

 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by leunam12 on 2016-10-15
If you can access the command prompt try to fix the bcd. Type the commands below and press enter after each command.

```
bootrec /FixMbr
bootrec /FixBoot
bootrec /ScanOs
bootrec /RebuildBcd
```

---

