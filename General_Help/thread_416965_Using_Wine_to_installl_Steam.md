---
title: "Using Wine to installl Steam"
date: 2007-04-21
forum: General Help
---

### Post by StevenAFC on 2007-04-21
Hey

Ive installed wine, added the font needed to the fonts folder, now when I try to execute 

wine msiexec /i SteamInstaller.msi

I get this error: 

err:msi:copy_package_to_temp failed to copy package L"SteamInstaller.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!

If i rename the steam file to Whatever.msi I get the same problems, so I'm assuming the file is in the wrong location? 

Where is wine looking when its executing a program?

Or theres something wrong with msiexec?

---

### Post by Drone4four on 2007-11-25
Hmm, $ wine msiexec /i SteamInstall.msi worked just fine for me.

---

### Post by Yellowdog428 on 2007-11-30
Yah you need to be in the directory where the file is located.  

Like if you downloaded to the desktop you need to be in the desktop directory in the terminal.

Cheers

---

