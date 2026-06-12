---
title: "Problem uninstalling Ubuntu (Installed through Wubi)"
date: 2008-07-08
forum: General Help
---

### Post by danieltharris on 2008-07-08
I downloaded and ran Wubi and did a 5GB installation to an external USB 2.0 HDD, formatted to NTFS.

It all installed and it added the boot option of "Ubuntu". However when I start it I get a load of error messages, but I can run some programs etc. I can login and open GIMP and Open Office etc but do receive errors all over the place.

I want to uninstall it, and then I am going to put it onto its own partition on my internal HDD. However when I am trying to uninstall it using the uninstall application nothing opens. I've restarted multiple times too and the program just doesn't start to uninstall. 

I've tried running the .exe directly and also used the Add/Remove programs interface :(

I think I got the original errors and this problem with not being able to uninstall because I put it onto an External HDD? I just want to get rid of it now so I can do a normal installation.

Is there any way to do this? Is this a common problem people have had with installing it?

---

### Post by PhaedrusDE on 2008-07-08
Recycling ago's advice to myself and others

[http://ubuntuforums.org/showpost.php?p=5340574&postcount=15](http://ubuntuforums.org/showpost.php?p=5340574&postcount=15)

---

### Post by danieltharris on 2008-07-08
Ah sorry about that. I should have searched but I was in a rush to post this during work time ;-)

---

### Post by solfire on 2008-07-08
This method doesn't work for me. The way that my laptop is partitioned, all the disc space is in D: therefore I installed Ubuntu to D:. I think this is where the problem is as it will not uninstall, despite using the uninstaller provided above.

---

### Post by goupi on 2008-08-22
Try this:
Remove C:\ubuntu (C:\wubi in 7.04) and C:\wubildr*. 

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block. 

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

It worked for me.  

Best, Goupi

---

