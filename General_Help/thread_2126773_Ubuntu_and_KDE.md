---
title: "Ubuntu and KDE"
date: 2013-03-18
forum: General Help
---

### Post by Chris62 on 2013-03-18
Hi,

I am running Ubuntu 12.10 on my dual boot Windows 7/Ubuntu machine and I found today when running the Software Updater that there was a lot of software to be downloaded for KDE. Surely, I do not need KDE software in Ubuntu so I am wondering why this appears in the software updater window. I have a laptop, also dual boot, that has the same version of Ubuntu and which is updated when the desktop machine is updated and this does not have anything to do with KDE in the updater window

Could anyone tell me why I am getting this and how to stop the software updater from displaying stuff to do with KDE if it is not necessary in Ubuntu

---

### Post by dabl on 2013-03-18
> **Chris62 said:**
> Hi,

Could anyone tell me why I am getting this and how to stop the software updater from displaying stuff to do with KDE if it is not necessary in Ubuntu

The updater (i.e. apt-get upgrade) only updates installed packages, including their dependent packages.  So you do have some kde package(s) installed, otherwise there would be no need to update them.

You can review your installed packages in the GUI package manager, and look for k......... named packages. Or open a terminal and check ```
sudo dpkg -l k*
```

---

### Post by mastablasta on 2013-03-18
or in other words you installed a programme that uses KDE packages. For example some game or somehting. and now it is updating the pakcages.


i installed Skrooge (money manager made for KDE) in windows XP. the programme takes about 12MB. it pulled in over 350 MB dependencies. and when i run pakcage manager they all get updated. i just like some KDE programmes. so not to waste the disk space i also installed various other KDE stuff (quassel and such) in windows...

---

### Post by Chris62 on 2013-03-19
Many thanks to you both. Running 'sudo dpkg -l k*' reveals a lot of files beginning with 'kde' such as 'kdebase-bin-kd' and 'kdelibs5-data-4:e.9.5-0ubu'. Presumably these are all to do with KDE but I am not sure why some have '0ubu'appended to them, so, I don't know whether to get rid of them to save disc space or just leave well alone. Presumably I could get rid of them by doing 'dpkg -r kde*', could I?

---

### Post by mastablasta on 2013-03-19
it is best to leave them if you have enough disk space. you could create a mess if you delete only some files. 

i htink the correct way would be to uninstall/remove all KDE based apps.

---

