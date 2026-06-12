---
title: "Dual Boot with Windows XP, will GRUB see an upgrade to windows?"
date: 2015-08-09
forum: General Help
---

### Post by Angela_C.Murphy on 2015-08-09
I have a Dell Dimension 4700, Pentium 4, 4 Gb memory, 2 hard disks: 160 Gb - Windows XP, and a 320 Gb with various partitions - extra space for windows programs and 2 forms of Linux, Xandros and Ubuntu. The 320 Gb is where my Ubuntu 12.04 lts resides.

I plan to upgrade my Windows XP to Vista, then to Windows 7, and I wish to retain my dual boot with Ubuntu.

Should I change GRUB manually, using GRUB Customizer, before I upgrade windows, or will GRUB make that change when I actually perform the upgrade?

Windows has a bad habit of trying to take over computers.  Since Ubuntu is really my primary operating system, I would be very upset if the windows upgrade messed up the MBR so that I could no longer boot into Ubuntu.

I use software, but I am in no way a software expert.  I need help on this.  I'd be very grateful for some advice from the Ubuntu community.

A.C. Murphy

---

### Post by Curtis_Anderson on 2015-08-09
I think the best way to go about this is to let Windows do its stuff (careful not to let it delete your other partitions) and then restore GRUB from a live session:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also, you may be better off by doing a clean install of Win 7 instead of upgrading twice, since doing so will typically leave a lot of garbage in the system.

---

### Post by yancek on 2015-08-09
I'm not sure why you would want to upgrade to vista then 7 rather than going directly to windows 7?  Could get really messy.  Installing windows has always overwritten any code in the master boot record without asking or notifying the user.  There have been numerous posts here recently with users upgrading to windows 10 and having Ubuntu unbootable so I expect upgrading earlier versions will have the same result.

---

### Post by Mark Phelps on 2015-08-09
> I'm not sure why you would want to upgrade to vista then 7 rather than going directly to windows 7?

Because ... MS doesn't allow you to do an in-place upgrade from XP to Win7; instead, you have to do a clean install, which means, you lose everything from XP in the process.

The Win10 problems, with which I'm personally painfully familiar, are exceptional -- and primarily due to MS having rushed a half-baked piece of garbage out the door LONG before it was ready for prime time.  Given the massive reporting of failed updates, it looks like MS put as little work into their upgrade software as they did their new, but incomplete, Browser named Edge.

---

### Post by oldfred on 2015-08-09
Do you have grub boot loader on Windows drive?
Much better with two drives to keep Window boot loader on Windows drive and grub on Linux drive.
And then set BIOS to boot grub. If issues with Windows you can still directly boot and possibly repair. Grub really only boots working Windows.

But if you are reinstalling a Windows make sure you have reset BIOS to default boot from Windows drive. Some cases Windows 7 has installed its 100MB boot partition to BIOS boot drive. And just overwritten the first 100MB of drive regardless of what Linux partition was there.

And that means you need really good backups of all your data in both Windows & Linux.

---

### Post by Angela_C.Murphy on 2015-08-09
Thanks, Mark Phelps - I am going to Windows 7 via Vista because I have nearly 10 years of installed software and downloaded upgrades in windows XP that would take many, many hours of work if I had to re-install them, if I even could.

To be clearer:  Windows is installed on Drive A. 
                       Ubuntu is on Drive B

There is an ntfs partition on drive B, which is for extra space for some windows programs and for the temp folder.  It is extended, not primary. All other partitions on drive B are Linux, an old Xandros, and my current Ubuntu and swap file.

GRUB is on both drives.  My computer uses MBR, and BIOS - I think it is too old for UEFI.

AC Murphy

---

### Post by Angela_C.Murphy on 2015-09-11
Luckily for me, at some point in the past, I had made a "Boot Repair Disk".  Of course the upgrade from Windows XP to Windows Vista messed up the boot process.  I then put in the boot repair disk and booted from it.  I followed the directions on the disk and rebooted.  Voila!  Grub was back and I now had a dual boot again, with the Vista loader in the place where Windows XP used to be.

Now I will have to do it all again when I upgrade Vista to Windows 7, but at least I have the boot repair disk.

Thanks for all the help.

---

