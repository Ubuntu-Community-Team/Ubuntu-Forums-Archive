---
title: "Help! After reinstallin Wubi one partition does not respond anymore"
date: 2007-06-22
forum: General Help
---

### Post by Danutz Nastase on 2007-06-22
Hi! I installed ubuntu through wubi on my computer that has Windows XP and two partitions (disks), C and E, both used with windows. I have now a big problem. Because I was not satisfied with the way Ubuntu was working I wanted to reinstall it again through wubi. I reinstalled it and now I cannot acces any longer the partition where wubi is installed, through windows, and ubuntu does not work at all. When I try to acces that partition through windows on the screen appears the message: " E:\ is not accesible. The file or directory is corrupted and unreadable".
     When I tried first to enter in Ubuntu I could log in, but then the computer refused to accept any command, the mouse did not respond.  
     If in the beginning I could boot in Ubuntu and then it did not work, now I can't boot any longer in Ubuntu. When I try to boot it appears on screen this message: "Error 17: File not found. Press any key to continue".
On the other partition Windows is working, but I have stored on the unaccesisible partition some things I want to have. So I have a big problem, especially because the "E" partition has a storage capacity of 60 GB and the other one only 20 GB.
Can anyone help me, PLEASE?????????????????

---

### Post by ago on 2007-06-22
Is the E: partition accessible from windows? What filesystem do you use? What version of wubi did you use?

---

### Post by Danutz Nastase on 2007-06-22
The E partition is not accesible through Windows and I made the huge mistake to move the "My Documents" directory into the E partition. I don't know what file system I use, because I am a new computer user, without much experience or knowledge in this field. If "ntfs"is file system, then this could be mine. As for the Wubi version, I can't tell you, because I cannot access the E partition, where the Wubi file is.

---

### Post by Danutz Nastase on 2007-06-23
When I installed Ubuntu through Wubi it worked. A few days I had no Internet connection, but after that suddenly my computer connected. So for about a week I had Internet connection in Ubuntu, but after that time the connection did not work anymore. So I decided to reinstall Ubuntu through the same Wubi version used for installing. I don't remember if Ubuntu was installed in English or in Romanian version, but when i tried to reinstall it I have chosen the Romanian language. And the reinstalling went O.K., but when I tried to enter in Ubuntu, I managed to log in, the screen of Ubuntu opened with the same GNOME theme i have chosen before reinstalling, but then I couldn't do anything. The cursor of the mouse was frozen on the screen, not reacting to what I was trying to do. So I managed to reset the computer and I entered in Windows, but there I was announced that "E is not accesible. The file or directory is corrupted and unreadable". The next day I tried to enter again in Ubuntu, but this time I could not even log in. On the screen appeared this announcement: "Error 17: File not found. Press any key to continue". So, this is the story.

---

### Post by ago on 2007-06-24
> **Danutz Nastase said:**
> So I managed to reset the computer and I entered in Windows, but there I was announced that "E is not accesible. The file or directory is corrupted and unreadable".

The filesystem is probably corrupted, did you hard reboot? You have to run checkdisk or similar from within windows to fix the errors.

---

### Post by CrazyGuy123 on 2007-06-24
Steps to run chkdsk are here:

Click Start, and then Run. 
2. In Open, type cmd and then press ENTER. 
3. To repair errors, at the command prompt, type
chkdsk E: /f
and then press ENTER.

You may have to restart the computer before the drive becomes accessible again.

It may help if you post the results when it's done.  To do that:
Click the icon in the top left of the Command Prompt window.  Choose Edit, and click Mark.  Draw a box around all the text by dragging the mouse around it.  When you're done press ENTER.  The text is now on the clipboard, and can be pasted into this website or another file.

---

### Post by Danutz Nastase on 2007-06-24
Guys, **THANK YOU!** 
You saved me. I did what you wrote me to and it worked. Now I can acces again the E partition and all my files are intact. Look at the report:

C:\Documents and Settings\UNU>chkdsk E:/f
The type of the file system is NTFS.

CHKDSK is verifying files (stage 1 of 3)...
Deleting corrupt file record segment 8096.
Deleting corrupt file record segment 9884.
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Correcting error in index $I30 for file 5.
Correcting error in index $I30 for file 5.
Sorting index $I30 in file 5.
Correcting error in index $I30 for file 2230.
Correcting error in index $I30 for file 2230.
Sorting index $I30 in file 2230.
Index verification completed.
CHKDSK is recovering lost files.
Recovering orphaned file $MFT (0) into directory file 5.
Recovering orphaned file $MFTMirr (1) into directory file 5.
Recovering orphaned file $LogFile (2) into directory file 5.
Recovering orphaned file $Volume (3) into directory file 5.
Recovering orphaned file $AttrDef (4) into directory file 5.
Recovering orphaned file . (5) into directory file 5.
Recovering orphaned file $Bitmap (6) into directory file 5.
Recovering orphaned file $Boot (7) into directory file 5.
Recovering orphaned file $BadClus (8) into directory file 5.
Recovering orphaned file $Secure (9) into directory file 5.
Recovering orphaned file $UpCase (10) into directory file 5.
Recovering orphaned file $Extend (11) into directory file 5.
Recovering orphaned file audio (107) into directory file 5.
Recovering orphaned file .Trash-unu (9858) into directory file 5.
Recovering orphaned file boot (9873) into directory file 2230.
Recovering orphaned file logs (10745) into directory file 2230.
Recovering orphaned file docs (10954) into directory file 2230.
Recovering orphaned file tools (10969) into directory file 2230.
Recovering orphaned file install (10970) into directory file 2230.
Recovering orphaned file license.txt (12608) into directory file 2230.
Recovering orphaned file UNINST~1.EXE (12728) into directory file 2230.
Recovering orphaned file Uninstall.exe (12728) into directory file 2230.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.
Correcting errors in the Master File Table (MFT) mirror.
Correcting errors in the master file table's (MFT) BITMAP attribute.
Correcting errors in the Volume Bitmap.
Windows has made corrections to the file system.

  57657253 KB total disk space.
  42938884 KB in 23832 files.
     10284 KB in 2417 indexes.
         0 KB in bad sectors.
     96193 KB in use by the system.
     65536 KB occupied by the log file.
  14611892 KB available on disk.

      4096 bytes in each allocation unit.
  14414313 total allocation units on disk.
   3652973 allocation units available on disk.

C:\Documents and Settings\UNU>

 I cannot thank you enough, I wish I could offer you at least a beer, but instead I can give you something that can go with the beer::popcorn:

---

