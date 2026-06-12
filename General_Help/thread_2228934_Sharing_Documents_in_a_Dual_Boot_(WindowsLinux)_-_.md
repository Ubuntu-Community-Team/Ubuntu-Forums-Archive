---
title: "Sharing Documents in a Dual Boot (Windows/Linux) - Is there a good solution?"
date: 2014-06-10
forum: General Help
---

### Post by 777funk on 2014-06-10
I started out with Ubuntu leaving the Windows partition as it was and using a new drive for Ubuntu then mounting Windows then using it's Doc folders for new data from Linux. This worked well, but it was risky since I was always modifying the Windows documents folders. This would result in a ChkDsk most Windows boots. *In other words*, Windows wasn't happy and I ran the risk of breaking something in the XP file system.

Fast forward 2 years later to today, I'm finally fixing things and will be relocating the Documents Folders to their own drive or at least partition. 

I've read that Linux can't access certain file information on NTFS partitions and of course Windows has trouble with EXT(x) partitions. So I'm torn on what to do. 
I do know that Ubuntu's Deja Dup stock backup software had trouble restoring any individual deleted files on the mounted NTFS shares. So there obviously was some trouble.

Is there a good solution to this problem (sharing Documents locations between the two OS's). I like to use Linux for the day to day but I also like the convenience of being able to access my files when I am booted into Windows.

Recommendations would be greatly appreciated!

---

### Post by oldfred on 2014-06-10
I never had an issue with a shared NTFS data partition with my XP. But that is now not used and I have not used the newest Windows 8. Its always on hibernation will cause issues like hibernation in Windows 7 would cause issues.
If you do not have fastboot in Windows 8 or any hibernation on in any Windows a shared NTFS partition should work.

Often better to set the Windows system (c: drive) as read only and the shared data partition as read/write. The Linux NTFS driver exposes all the normally hidden files & folders in Windows. With XP I would always turn on seeing all the hidden files & folders and many times corrupted something I should not have. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by 777funk on 2014-06-11
I remember what I read. Linux has problems with preserving permissions in NTFS. Maybe that's what it was. I also had issues with Deja Dup backing up single files from an automount location with NTFS for some reason.

---

### Post by oldfred on 2014-06-11
If sharing data there is no issue of permissions. 
It is just that Windows NTFS does not support Linux type ownership & permissions.

But ownership & permissions is required for any system file including /home, but not your data inside /home but configuration files maybe. Or permissions for data can be easily reset with one common setting, where permissions and ownership for system files can be many different settings and you lose those settings if any system file is copied to NTFS.

---

