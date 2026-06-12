---
title: "Grub missing??  Can't boot my laptop!"
date: 2017-11-27
forum: General Help
---

### Post by dryan775 on 2017-11-27
Hello all,

Thanks in advance for any assistance.

My Toshiba laptop has been set up for dual boot for some time (Windows 10 and Ubuntu 16.042 LTS Gnome3).
I rarely shut it down from Ubuntu, put it to sleep at night and wake it up when I need it.

I actually Needed something in Windows, so I shut down Ubuntu and when it booted back up, the Toshiba splash screen sat there for an unusually long time, then i got this error message:  "Reboot and select proper Boot device or Insert Boot Media in seleted Boot device and press a key"

No idea what happened.

I can reboot, kit F12 and get into BIOS
I can boot from my Ubuntu 16.04 LTS LiveDVD with Gnome2 MATE enviornment.  
Within that enviornment, I can see both the windows and Ubuntu partitions, I can browse the Ubuntu partition, but my home folder's permissions don't let me look around.

I'm thinking Grub was damaged/destroyed somehow and now BIOS doesn't see it as a bootable volume.

Any idea how to fix this from withing the Ubuntu 16.04 Mate enviornment?

Thanks!

DwR

---

### Post by westie457 on 2017-11-27
Hi before any repair suggestions are made could you boot your Live DVD and go here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Scroll down to the '2nd option' and follow the instructions there. When the 'Boot Repair' windows opens **do not **click on repair automatically, instead click on 'Create Boot info report', post the generated link back here.
Further advice and options will follow in due course.

---

### Post by dryan775 on 2017-11-27
Ok, it ran forever, but here is the link:

[http://paste.ubuntu.com/26062140/](http://paste.ubuntu.com/26062140/)

---

### Post by oldfred on 2017-11-27
It looks like you booted live installer in BIOS mode as it wants you to add bios_grub partition and install grub in BIOS boot mode. But you have UEFI system, UEFI Windows and an UEFI install of Ubuntu. Always boot in UEFI mode.

It probably took a long time as you show partition issues and it had to time out.
You show both ESP (sda2) as unknown, and Windows NTFS partitions shown as hibernated, not sure if ESP issue is from hibernation or separate issue.

Can you still directly boot Windows from UEFI (f12) menu? Grub will only boot working Windows, or Windows that is not hibernated. And since you had not booted into Windows for a while, it probably ran updates and is known on major updates to turn fast start up back on.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If you cannot boot Windows then you may need the fixes on sda2 first. Normally since FAT32 you can run Windows chkdsk or Ubuntu dosfsck.

 Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by dryan775 on 2017-11-28
I understand the basic difference between BIOS and EFI, but I didn't think i got a choice.
I put the Live DVD in, and it boots.  I didn't see any options in the [I'll call it] BIOS setup screen to select boot order that said anything about booting using BIOS or EFI.  I just seemed to work.

Can I still boot windows?  
No.  the system goes straight to the error message if I even attempt to let it boot from the HDD.  
If I turn off and reboot, pressing F12, I can get back to the system setup screens.  My only option to get a usable system is the Live DVD.

Boot mode (in system setup) is set to UEFI mode
Secure boot mode is disabled

Just before it cracked I WAS able to see the Windows partition, I make a point of logging off Windows the shut down from the account selection screen, so it shouldn't have been in hibernation mode.  

I had backed up fairly recently, so I wouldn't loose anything important if I just wiped the drive and installed Ubuntu on a single partition, I don't really want to spend a lot of time on this project.

---

### Post by yancek on 2017-11-28
Just doing a 'full shutdown' from windows won't turn off fastboot/hibernation.  Read the links posted by oldfred.
If you have your windows recovery disk, you should be able to boot that and select the Repair option to run chkdsk.  Can't be done from any Linux.  You might try the dosfsck command posted by oldfred from an Ubuntu terminal on the Live DVD.

---

### Post by dryan775 on 2017-11-28
OK, Windows as annoyed me for the last time on this machine.  I was able to retrieve the few Windows files I needed.
I do still have a FEW files in my Ubuntu home folder that I need to retrieve before wiping this machine completely, one partition for Ubuntu.

How an I access that folder with the permissions restrictions?

---

### Post by dryan775 on 2017-11-28
nevemind, got it!

Goodbye Windows!

---

