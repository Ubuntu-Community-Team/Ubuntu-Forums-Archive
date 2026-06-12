---
title: "How to install Rainlendar calendar's skin in ubuntu 12.10 ?"
date: 2012-12-27
forum: General Help
---

### Post by sinaphysics on 2012-12-27
Hello,
I installed the Rainlendar calendar in ubuntu 12.10. Indeed the software works great but I have problem in installing new skins which are zip type.

> How can I install skins or languages?
Written by Kimmo Pekkola 
There are two kinds of skins for Rainlendar: The old skins which are usually distributed as a zip or rar archive and the new skins which have .r2skin extension.
 
To install old skins you need to uncompress the skin into the Rainlendar's skins-folder. Make sure that no extra folders are created when you unzip the archive. There must be only one subfolder under the skins-folder where the skin's ini-file(s) are located. After you refresh the calendar the skin should appear in the skin list. If that doesn't happen check the Rainlendar's log file for possible errors.
 
Note that there are two places where the skins can be copied. They can be either in Rainlendar's program folder (which in Mac is inside the application bundle) or in the settings folder. In most cases you should copy the skin to the "skins" folder which is in the settings folder. Note that the "skins" folder doesn't exist unless you have already installed skins before but you can also just create it manually.
 
To install new skins (.r2skin) you can just drag and drop the file over one of the Rainlendar's windows and it will be installed automatically. In Windows you can install the skin also just by double clicking it. The languages (.r2lang) can be installed the same way as the new skins (i.e. by double clicking or dropping).
 
Note that if your web browser tries to suggest a different file extension for the new format skins instead of the ".r2skin" you need to rename the file back to its original form. But do this only if the original file had ".r2skin" extension. Renaming old format skins will not make them automatically installable.
 

Actually I did exactly what said in this guidance. But it doesn't work for me. The .r2skin works well but zip no. My skin folder is  located in " /usr/lib/rainlendar2/skins ". what do u suggest ?

---

### Post by sinaphysics on 2012-12-27
I find the problem. Actually the problem is in path. I find path "/home/sina/.config/.rainlendar2/skins".

---

