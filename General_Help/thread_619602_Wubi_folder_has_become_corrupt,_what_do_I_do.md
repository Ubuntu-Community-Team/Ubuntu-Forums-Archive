---
title: "Wubi folder has become corrupt, what do I do?"
date: 2007-11-21
forum: General Help
---

### Post by mike868y on 2007-11-21
I have been using wubi for a little bit and have been loving it however I believe that my C:/wubi folder has become corrupt. When i go to boot into Ubuntu it tells me that it cannot find a certain file in C:/Wubi (i forget which file exactly). So, I went into windows to attempt to find the file in C:/Wubi. When i try to enter this folder Windows gives me the error message "The file is corrupt and unreadable." So, I went to delete the folder and windows tells me that I canot becuase the directory is not empty. So, I went to uninstall it from Add or Remove programs and I get the error message from the system tray "Teh File or directory C:/wubi is corrupt and unreadable. Please run the Chkdsk utility. So, I went to run and ran chkdsk, and it didn't seem to help. So i redownloaded the installer and it gives me the error message "error opening file for writing: C:/Wubi/license.txt Retry to try again or ignore to ignore this message. So i ignore the file, and It continues to tell me the same error message for different files. So, I appear to be in an endless loop of errors. I cannot boot, I cannot uninstall, and I cannot reinstall. What do I do?

---

### Post by mike868y on 2007-11-21
bump

---

### Post by ago on 2007-11-22
chkdsk /r

---

### Post by mike868y on 2007-11-22
I ran a chkdsk but it diddn't help. What is the difference between chkdsk and chkdsk /r?

---

### Post by Tom Mann on 2007-11-22
Click start and run.

In the run box type cmd.exe

try the following:

rd /s C:\Wubi

(this command would try to delete c:\wubi and all of it's contents)

if that doesn't work repeat the above switching cmd.exe with command.exe


if neither of them work, boot into safe mode and try the above from the start.

if that fails... try booting an ubuntu live cd, locate your disk in "computer" in the places menu, and try to delete the Wubi folder.
(I can't guarantee this working but the theory is OK!)

We offer help for Windows here too :)

Tom

---

