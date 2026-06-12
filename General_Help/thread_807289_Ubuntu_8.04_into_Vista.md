---
title: "Ubuntu 8.04 into Vista"
date: 2008-05-25
forum: General Help
---

### Post by bathhm on 2008-05-25
Trying to install Ubuntu 8.04 into Vista.  Wubi is being run from a copy on c:\ in Vista, with verified OK CD in CDROM drive.  Immediately after answering the 6 questions and hitting a "continue", I get the message in a window "Error opening file for writing c:\ubuntu\winboot\wubildr.exe"  And it gives 3 choices, Abort, Try Again, Ignore.  If Ignore, install proceeds with checksum and downloading and instruction to reboot.  But no Ubuntu vs Windows option appears.  Same behavior with wubi.exe from the CD or wubi-8.04.exe downloaded from wubi-installer.com.  Can the fact that the Vista install has been backed up with Acronis?  Any input greatly appreciated

---

### Post by Dave2k6 on 2008-05-25
Right click on the ubuntu folder and check if 'Read Only' is unticked (means files can be written to). Also check security tab to see if your user id/group has the correct privledges to that folder, subfolders and files

---

### Post by bathhm on 2008-05-28
> **Dave2k6 said:**
> Right click on the ubuntu folder and check if 'Read Only' is unticked (means files can be written to). Also check security tab to see if your user id/group has the correct privledges to that folder, subfolders and files

I think you have hit the nail on the head.  /ubuntu/winboot is indeed write protected.  So now I have to learn about Vista's security features. All the same, Vista behaves very differently, for me, than XP in that when the Live CD is put into the CDROM drive the Wubi window with the three choices does't appear, and the two choices presented don't work.  A properly partitioned HD with dual boot looks easier and easier.

---

### Post by Dave2k6 on 2008-05-28
Right click on /ubuntu/winboot and make sure you'r on Geneal tab, then look in Attributes section and untick Read-only box and click IK to apply changes. This removes the write protected status on that folder and everything inside it.

---

