---
title: "Directory Recovery Suggestions Requested"
date: 2021-02-07
forum: General Help
---

### Post by martrw on 2021-02-07
I was switching between OS on dual boot hard drive, Windows7 and Kubuntu 20.04.  I copied a data directory from the Win7 partition to the Kubuntu 20.04 Documents directory for backup purposed. Documents was whole and intact at this time.  I rebooted into Win7 to print a file and after having driver issues with the printer, switched back to Kubuntu to print from Linux.  At this point I discovered that the entire Documents directory has disappeared.  I immediately shut down the hard drive and booted back up on a spare drive to try and recover the Documents directory.

Using testdisk and R-linux from the spare drive and examining the corrupt drive, there is no record of a Documents directory anywhere.  Deleted files from other directories can be seen and recovered, but there is no trace of the Documents directory.

I would really appreciate some help with this one.  Although I have a backup of the bulk of the data which was in Documents, there are several recent documents representing a lot of effort which haven't been backed up yet.

Hope someone has seen this before.

**Update 02/07/21 1700hr**
Two files were deleted from Downloads directory around the same time as the Copy/Paste from Windows OS to Documents was executed, approx 0848 hr.  These can be seen with R-Linux.  R-Linux shows 20 deleted inodes in the root directory in the 0843 to 0845 timeframe.  debugfs shows 0 deleted inodes in either the root directory or the /home directory.  The /home directory contained the Documents folder.

**Update 02/08/21 0217**
Had a backup image of the /home folder and compared it to the corrupted drive.  Using Dolphin Properties the image(which contains an old version of the Documents folder) /home had 51.5 GiB, 62,283 files and 5836 subfolders.  The newer /home folder(with missing Documents) had 34.2 GiB, 85,234 files and 8279 subfolders.  There is clearly something corrupt with the newer /home file structure

---

### Post by TheFu on 2021-02-07
You claim 
> Documents was whole and intact at this time.
How did you copy the files over? How did you check they were "intect"?  From Windows or from Linux?
Which file system was used?

---

### Post by martrw on 2021-02-07
Copied files using copy/paste from Dolphin.  There was no check other than visual familiarity with the directory structure.  I saw and recognized where I was, I looked into the pasted directory and saw the file structure and names I was familiar with and exited Dolphin.  Files were copied from Windows directory to Linux directory while in Linux operating system.  Ext4 is linux, NTFS is Windows file system.

---

### Post by TheFu on 2021-02-07
Very helpful. Thanks.

Those answers removed any ideas I had.

---

