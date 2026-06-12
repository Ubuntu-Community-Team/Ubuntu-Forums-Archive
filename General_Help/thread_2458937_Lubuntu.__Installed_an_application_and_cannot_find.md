---
title: "Lubuntu.  Installed an application and cannot find it anywhere even after reboot"
date: 2021-03-06
forum: General Help
---

### Post by autonenterprises on 2021-03-06
Hi,

thanks in adavance.

I opened the package manager, synaptic I believe, and installed a DICOM viewer called dicomscope. I verified after reboot that it is installed via the package manager but I cannot find it in any menu listing and the "search" in the menu will not find it either.

Any ideas. Once I find it I have to verify it works and add a panel shortcut. I can only imagine how fun all of that is going to be.

---

### Post by yetimon_64 on 2021-03-07
Try the command...
```
which dicomscope
```
... in the terminal. That should pick up the location of a newly installed applications executable. This applies only if the executable is named the same as the package, which is mostly the case but not always.

Another possibility since you have it installed, you can use synaptic again, highlight and right click the dicomsope entry in synaptic and choose "Properties". You can then go to the "Installed files" tab and look to see where dicomscope places any of its files including the executable and any desktop configuration files. If no desktop config file is supplied then it is easy enough to create one, as it is a simple text file, and store it in ~/.local/share/applications.

If the executable is in the system path then using just the application name in the terminal should launch it if you haven't got a desktop config file (.desktop file) provided. Not all applications supply a desktop config file and if the case will not show up in the desktop environment menus, this is normal behaviour for such applications.

> I have to verify it works and add a panel shortcut That wording seems to indicate this is some sort of homework/studies assignment etc. Is this the case?

---

### Post by guiverc on 2021-03-07
You haven't said what release of Lubuntu, however the last *five* releases of Lubuntu have provided both *Discover* as the Software Centre and the **Muon** Package manager.

[https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html](https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html)

I don't know the program, nor your release ([https://packages.ubuntu.com/groovy/dicomscope](https://packages.ubuntu.com/groovy/dicomscope) but your release may differ) but the Lubuntu manual page for adding desktop icons (shortcuts) can be viewed with

[https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html](https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html)

---

