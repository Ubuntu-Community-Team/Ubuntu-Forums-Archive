---
title: "How to save screenshot in Ubuntu LiveCD?"
date: 2013-08-15
forum: General Help
---

### Post by peter1897 on 2013-08-15
When i load Ubuntu LiveCD i select Try Ubuntu but when i take a screenshot how can i save it so after this to use it in windows. I try to save it on some of the ntsf partition or Ubuntu disk but when i load Windows the screenshot is not neither on the partition or CD disk.

---

### Post by westie457 on 2013-08-15
Have you shut Windows down or have you put it into suspend or hibernation?

Windows must be fully shut down for any file-system changes to take effect. When writing files to the main Windows partition (c: drive) if the system is not fully shut down the changes are not written to the Master File Table and Windows will ignore the changes.

Having said that, it is more recommended to have a separate data partition formatted as NTFS so it can be read by Windows and just about any other OS.

IDK if the data partition will suffer the same fate if Windows is suspended as I always shut down only.

---

### Post by peter1897 on 2013-08-15
What do you mean by shut down Windows? I insert LiveCD then restart Windows, then when Ubuntu loads i take screenshot and save it in partition on which Windows is not installed, then i shut down Ubuntu and power up the laptop after this.

I don't know if Ubuntu is suppose to work with ntfs drives because it only recognizes my ntfs partitions but if i try to open some of them it can't open it.

---

### Post by westie457 on 2013-08-15
There could be a problem with the file-system that is preventing files being written to the partition.

Force a chkdsk /f of the drive.

In Windows click the Start button > (My)Computer. Right-click the drive having the problem select properties. In the pop-up window select the Tools tab and then Check drive for errors. After that you should be able to carry on with what you are attempting to do.

The Linux tools will not do a proper job of correcting any errors in the file-system.

If you are still unable to save to that drive/partition then we will continue with the way the computer gets shut down.

---

### Post by Cokaric on 2013-08-15
If that fails... Try to

a) save it to usb
b) save it to www (email, webpage, ftp, cloud storage, etc...)
c) run ubuntu in VMware parallel with with Windows

---

### Post by peter1897 on 2013-08-15
I run error check on the drive from windows explorer and from command prompt and it didn't find errors. Then i load again the LiveCD and this time i was able to save the screenshot on the drive. I think the first time it didn't work because the drive was not mounted.

---

### Post by erasmusp on 2013-08-15
I am surprised that it pretends to save a file onto a drive that is not mounted without giving you any error message - sure it was not something else perhaps?

---

### Post by peter1897 on 2013-08-15
I tried 3 times without success. I was just pointing the save location to the drive and click save, it didn't give me any error message. I use the screenshot program that is in Ubuntu 12.04.
After i run the error check i opened first the drive and then i was able to save the screenshot. Before running the error check i couldn't open the drive, i don't why.

---

### Post by peter1897 on 2013-08-15
Another problem. I can't open the screenshot image in Windows. I tryed with Windows Photo Viewer, Paint, Photoscape - none of theme could open it. I can't even edit the file, if i try to rename it is says the file name is not valid. The image is in .png format.

Edit: The problem was in the semicolon sign ":" that Ubuntu put in the image file name.

---

