---
title: "Cannot access folder Ubuntu 17.10"
date: 2018-02-25
forum: General Help
---

### Post by carusoswi on 2018-02-25
I have a folder that happens to be on an external drive which is misbehaving.  If I click the caret to the left of the folder name, a dropdown shows that lists the names of the files inside the folder.  I can click on files to open them.  If I doubleclick on the folder name, I can an input output error message.  I have tried to create a folder inside that folder, and that fails also with the same error message.

So, obviously, my data still resides inside the folder, and I can still access it, just cannot click on the older to open it.

No other problems with any other files on the drive which is a new 3T external drive connected via usb.  I have tried rebooting, demounting/remounting the drive.  I am stumped.

Suggestions would be appreciated.  My laptop dual boots (Ubuntu/Windows 10), so I think I will try booting into windows and try accessing this folder from there.  

The data in the folder is just some 33 image files that still reside on the memory card from which I copied them, so no hysterics here.  The data is safe, and these photos are not all that important, either.  I would like to take this opportunity to see if I can fix the problem so that I would know what to do if it happens in a situation where the data is important.

Thanks for any suggestions.

Caruso

---

### Post by carusoswi on 2018-02-25
So, I booted into Windows 10 where I can click into this folder to open it without a problem.  When I boot back into Ubuntu, the problem is still there.  I can still click the caret and the file names drop down and I can double click to open them.  This seems very odd.  I could just boot back into Windows, delete the folder/files, re-create the folder and import the files again.  But, I would really like to learn what might be going on here.

Again, thanks for any suggestions.

Caruso

---

### Post by wildmanne39 on 2018-02-25
Did you remove the drive safely from windows before you shut windows down and booted ubuntu? usually a input/output error means there is an issue with the drive but since you can access it on windows makes me think maybe it was not safely removed, if it was not you will have to boot windows and remove it safely then boot ubuntu and it may work if no damage has been done.

---

### Post by carusoswi on 2018-02-25
Thank you for your reply.  I generally never remove this external drive from Windows because it also houses my Dropbox data (Dropbox does not support the use of external drives, but I have found that as long as you do not run Windows when the Dropbox folder is not accessible (as when the drive is not present), then there is no problem storing the Dropbox folder on the external drive).

I think more to the point of my problem is the fact that all the other folders on this drive are working fine in both OSs.  This folder was working fine until just recently.  I cannot safely try your suggestion because, when Dropbox doesn't see files on that external drive, it makes the assumption that I have deleted the missing files and proceeds to start deleting them in the cloud.  One can recover the cloud-deleted files, but who needs the hassle.

I'll wait for a few more suggestions, and, if I do not find something to fix the folder, I'll just boot into Windows, delete it, and forget about it.  I have already created a new folder to replace the problem one, and have copied the affected files from my camera's memory card to the new folder.

I do thank you for taking the time to offer your suggestion.

Have a great day.

Caruso

---

### Post by carusoswi on 2018-03-04
So, the problem was solved by running chksdk with the /f switch in Windows 10. I hope this helps anyone else who encounters this problem.
Caruso

---

