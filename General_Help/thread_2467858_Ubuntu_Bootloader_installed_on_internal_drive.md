---
title: "Ubuntu Bootloader installed on internal drive"
date: 2021-10-09
forum: General Help
---

### Post by Sandi1987 on 2021-10-09
I installed Ubuntu on external SSD but "Ubuntu" Bootloader is on my internal NVMe SSD. I have Windows on internal SSD.

---

### Post by kurt18947 on 2021-10-10
You should have been able to choose where it goes during the install process. It's been some time since I've done an install - LTS user - perhaps one must use the "something else" option when choosing where to install. My sometimes faulty memory says there are 3 choices during the install process. 
1) Install beside an existing OS, often Windows 

2) Overwrite whatever is on the drive

3) Something else where the user can choose to install. If installing to other than the primary drive the boot files will still be placed on the the primary drive unless told otherwise. This sounds like this is what you have. Somewhere on the "something else" screen should be a way to choose where the boot files go. Sorry I can't be more specific, as I said it's been a while since I've done this.

---

### Post by tea for one on 2021-10-10
The Ubuntu installer has an irritating bug/feature where it will use the first EFI partition it finds.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

_Suggestion_

Boot into Windows
Unmount external drive cleanly
Fix Windows Boot Manager (if necessary)
Double check by rebooting Windows to ensure it is OK

Remove, isolate or de-activate internal Windows drive
Attach external drive
Boot Ubuntu installer in UEFI mode
Install again and Ubuntu will create a separate EFI partition on your external drive

You should be easily able to boot either OS from your UEFI boot menu (rather than Grub)
Always have backups available before crucial operations involving installations/partitions etc.

---

### Post by yancek on 2021-10-10
The original post in that bug report is nearly 7 years ago so I doubt Canonical developers are going to change it.  There are ways to fix this such as the method posted above but for a new user, it's repair it after the install.  It's difficult for a new user to know or expect something like this is going to happen.  A user could copy the ubuntu directory on the windows drive to the EFI partition on the Ubuntu drive but then would need to change the /etc/fstab file entry for EFI.  Probably need to reinstall Grub on the Ubuntu drive.

For users who are familiar with Linux/Ubuntu, this is an irritation but for new users, it is much more than that and I am sure there are many who have just given up and gone back to windows.

---

### Post by tea for one on 2021-10-10
@yancek

There may not be an EFI partition on the Ubuntu drive, which makes a repair more complicated.
I agree that the current installer will probably not be fixed but there is a new installer in Ubuntu 21.10.
I haven't used the new version yet but I hope that the existing problem has been eliminated.

---

### Post by dragonfly41 on 2021-10-10
There is a workaround. Install rEFInd on the external SSD. Or indeed on the main drive if preferred.

---

### Post by zorin1 on 2021-10-13
> **yancek said:**
> The original post in that bug report is nearly 7 years ago so I doubt Canonical developers are going to change it.  There are ways to fix this such as the method posted above but for a new user, it's repair it after the install.  It's difficult for a new user to know or expect something like this is going to happen.  A user could copy the ubuntu directory on the windows drive to the EFI partition on the Ubuntu drive but then would need to change the /etc/fstab file entry for EFI.  Probably need to reinstall Grub on the Ubuntu drive.

For users who are familiar with Linux/Ubuntu, this is an irritation but for new users, it is much more than that and I am sure there are many who have just given up and gone back to windows.

I ran into this problem the other day myself with both 21.04 and 20.04 LTE.  It just installed into the first EFI partition which happened to be Windows for me.  Basically, in windows, I mounted both both the internal and external UFI partitions.  The Ubunti external drive UFI partition was empty.  After it both were mounted, I just copied from the Windows UFI /EFI/ubuntu to the Ubuntu EFI /EFI/ubuntu.  Then when I boot the bios sees ubuntu on the external and internal drive.  I select the internal drive and then fix /etc/fstab to mount the external disk.  Then reboot, and go to windows and mount the Windows EFI again and delete ubuntu directory from the EFI folder.  

This is just a pain and not sure if I'm doing everything correctly.  So my question is how do you do the EFI repair?  Either way, the fstab is messed up so I'm not sure if the repair will work without first fixing that.  

This bug really needs to be addressed, does not make sense that it is not installing on the right drive.  Even if you do a manual partition and tell it where to load it still does not work.

This is going to be really frustrating for a new user that just wanted to try out Linux.  I know if that I would have ran into this problem, I would never try Linux again.  Who has time to do all the research to figure this stuff out, it should just work.

---

### Post by yancek on 2021-10-13
> Either way, the fstab is messed up so I'm not sure if the repair will work without first fixing that.  
 

You will need to fix that as the fstab file will show /boot/efi mounted on the internal windows drive.  You have to boot into Ubuntu or use a live cd/usb to change the entry so that it points to the efi partition on the external drive.

> This bug really needs to be addressed 

Good luck with that.  The Ubuntu developers have had this method for 7 years and despite all the complaints from users, have seen no inclination to change it,

>   Even if you do a manual partition and tell it where to load it still does not work.

No, it doesn't and that is by design by the developers.

> I know if that I would have ran into this problem, I would never try Linux again  

You're confusing Linux with Ubuntu.  Before Ubuntu existed, Linux had been around for well over a decade.  This problem appears to be strictly related to Ubuntu and the installer.  I've installed other Linux OS's UEFI Iwithout this problem.  There are hundreds of different Linux OS's and the link below has information on a few of them if you are interested in trying something else.  I will say that complaining here at the forums isn't productive as the forum and its users have no control over what the Canonical developers do or don't do.  Good luck with your Ubuntu.

[https://distrowatch.com/](https://distrowatch.com/)

---

### Post by grahammechanical on 2021-10-13
To anyone reading this thread and thinking about dual booting Windows and Ubuntu with Windows on one drive and Ubuntu on another drive. Remember to disconnect the Windows drive. When the installation of Ubuntu is finished and found to be working correctly - reconnected the Windows drive and then load Ubuntu and run this command.

```
sudo grub-update
```

If you boot from the Ubuntu drive you will then see a boot menu (Grub) that will offer to load both Ubuntu and Windows.

Regards

---

