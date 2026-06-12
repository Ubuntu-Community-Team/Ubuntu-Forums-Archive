---
title: "Can't access my External WD Passport HDD B/C of a checksum error"
date: 2015-04-05
forum: General Help
---

### Post by ted13 on 2015-04-05
[FONT=Segoe UI]**Background info: **
I have a mid 2012 13" macbook pro running Mavericks that started to have HDD slow downs. As a precaution, I backed up my user data to a 2TB western digital "my passport" hard drive (formatted in exFAT). A couple days after performing this backup, my macbook pro died. Note: I did not use time machine, I just saved my data from the users folder.

[/FONT]
[FONT=Segoe UI]After my macbook pro died, I started using a temporary laptop that is running Ubuntu 14.04. I had successfully mounted the "passport" drive just days ago to retrieve a file and everything worked fine.

[/FONT]
[FONT=Segoe UI]**Problem: **
But today, when I finally had time to properly reduplicate the user data from the "passport" drive to another backup drive... of course, the passport drive is no longer mounting. It gives me the following error message:

[/FONT]
> 
[FONT=Segoe UI]Error mounting /dev/sdb1 at /media/rbuse/My Passport: Command-linemount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,e rrors=remount-ro,umask=0077" "/dev/sdb1" "/media/rbuse/My Passport"' exited with non-zero exit status 1: stdout:FUSE exfat 1.0.1 

' stderr: ERROR:._.com.apple.timemachine.donotpresent' has invalid checksum (0x6634 != 0x4044). '[/FONT]
[FONT=Segoe UI]

Note that I can see the passport drive listed in the Devices section of Files. But when I click on it, it pops up a window with the above error message.[/FONT]
[FONT=Segoe UI]
What can I do to get it to mount properly?[/FONT]

---

### Post by WunNation on 2015-04-15
I was getting the same error message today when plugging my WD MyBook in to my Ubuntu 12.04 System.
This happened after I let a friend use my drive on his macbook (who knows what he did :) ).

I found the answer to this problem here.
[https://bbs.archlinux.org/viewtopic.php?id=168832](https://bbs.archlinux.org/viewtopic.php?id=168832)
by 'saigon' in one of the last posts.

The  easiest solution is to plug the Drive back into the Apple Mac OS X Machine  (especially since the problem appeared to originate with Apple's Time  Machine)
- If the drive automatically mounts to the Desktop, 'Eject' the Drive. (right-click on the desktop icon for the drive, if it's there, and select 'Eject')
- Open 'Disk Utility' on OS X
-- In Disk Utility, Click on the Drive/Partition that is throwing this error in the left hand bar
Click 'Repair Disk'
During the 'Repair' Process.
The error should be detected as, "Incorrect checksum for directory entry set".
The solution should be reported as, "The volume was repaired successfully".

After completing these steps, I was able to use my MyBook on my Ubuntu laptop again without any errors.

---

