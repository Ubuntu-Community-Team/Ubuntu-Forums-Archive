---
title: "Ubuntu and NTFS"
date: 2013-07-13
forum: General Help
---

### Post by EricKit on 2013-07-13
A really quick question on why Ubuntu doesn't get along well with NTFS.

I have Windows 8 installed and Ubuntu installed.  I link my Ubuntu to my Windows Documents/Pictures/Videos, but whenever Ubuntu makes a new file, Windows doesn't detect it.  I have to repair this drive twice in Windows for the Ubuntu files to show up.

I know there are other solutions, create a FAT partition that both can access, delete Windows 8 :), etc.  I'm not looking for a solution to fix this problem, I'm more just looking to understand Ubuntu's interaction with NTFS better.  My understanding is that Microsoft is constantly changing the NTFS specification without publication and it just doesn't make sense for Ubuntu to keep up.

---

### Post by oldfred on 2013-07-13
Do you still have hibernation turned on in Windows? That in effect reverts file info to as it was when you shutdown, so no changes are recognized. 
Better to have a separate shared NTFS data partition, but even then do not have it mounted in Windows when you shutdown or it will have the same issue. Best not to hibernate when dual booting. Same issue if dual booting Windows 7 and Windows 8. So it is not Ubuntu but Windows.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by EricKit on 2013-07-13
So you're saying that Ubuntu knows how to write to a file system NTFS just fine.  It's strange that whenever you navigate to a new file structure each time in Windows it wouldn't look to see what files are in there each time.  A "Refresh" should tell it to look in the folder so that if would show all new files.  Since the entire file structure is not stored in RAM  why would a hibernate effect that?  I just don't fully understand.  

That being said, I don't user hibernate, but Windows 8 when you shutdown is actually not a real shutdown... to get a full full traditional shutdown you have to reboot windows.  That's why Window's 8 won't run updates on a shutdown but only on a restart.  This is all part of the Windows fast boot.  I wonder if I disable the fast-boot function if that will help.  EDIT: I just attempted to do a full reboot, no hibernates, created new files... Windows still doesn't detect them.  Some of the things I read on it are here:> Any NTFS partition is **NOT** fully stable when written to, when the background 'Windows file manager' is not running.  This is NOT an absolute, as just editing an existing file may not cause a problem.  However, creating a new file or radically changing the size of a file will sometimes cause problems.
There is more than one method (for performance advantage?) to add extra NTFS blocks, etc. and Windows may arbitrarily 'assign' a method.  There is also anecdotal evidence that NTFS has changed slightly (and repeatedly) for each Windows service pack (and major release).
When you write to an NTFS partition, and then re-start Windows, this can automatically trigger a CHKDSK run.  This will also occur if you re-size the partition.
A given implementation of NTFS may not handle a partition in the exact same manner as another.  This still means that an NTFS partition solely under the control of Linux should **NOT** cause issues.
noted elsewhere:
[http://www.justlinux.com/forum/showpost.php?p=527739&postcount=3](http://www.justlinux.com/forum/showpost.php?p=527739&postcount=3)  
[http://www.knoppix.net/wiki/Using_FAQ#Q:_How_can_I_write_data_on_NTFS_partitions.3F](http://www.knoppix.net/wiki/Using_FAQ#Q:_How_can_I_write_data_on_NTFS_partitions.3F)
**Conclusion:** *Writing to NTFS **should** be possible, and **should** cause no issues. However, until better documentation and standards are available this may still **cause problems** ..*
That was from: [http://askubuntu.com/questions/84101/seeing-ubuntu-made-files-on-an-ntfs-partition-from-within-windows-7](http://askubuntu.com/questions/84101/seeing-ubuntu-made-files-on-an-ntfs-partition-from-within-windows-7) and I'm just trying to find a more technical reasoning to why this happens.  It's a known issue that Windows sees these files as corrupt.  Thanks for the help in understanding this.

---

### Post by sgage on 2013-07-13
I have never had any trouble with ntfs, in many years of dual-booting with Windows 7 and Windows 8. However, as mentioned, Windows 8 has a hibernation feature to facilitate faster booting. This has caused the partition not to be mounted under Linux, since Linux will think it's in use, I always create an entry in fstab for my Windows partition, and if it's Windows 8, add the 'remove_hiberfile' option. No problem.

---

### Post by coffeecat on 2013-07-13
Not specifically an Ubuntu +1 thread (U+1 forum is for "the discussion of the development of the next version of Ubuntu.")

*Thread moved to **General Help**.*

---

### Post by EricKit on 2013-07-13
Thanks for moving it.  Update to it.

Tried to run a dskchk and it deleted all the files I had created.  There was no hibernation or fast boot being used.

---

