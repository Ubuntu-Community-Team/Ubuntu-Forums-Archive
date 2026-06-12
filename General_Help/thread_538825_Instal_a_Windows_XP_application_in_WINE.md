---
title: "Instal a Windows XP application in WINE"
date: 2007-08-30
forum: General Help
---

### Post by rdoolen on 2007-08-30
I want to install an app with wine. When I run the installer, it won't install and says it can only be installed in Windows XP or 2003.

IS there a way to make WINE appear to be XP, or someother way to get this to install.

---

### Post by SPr on 2007-08-30
In a terminal enter:
winecfg

There is an option of different Windows OSs in the wine config panel.

---

### Post by kellemes on 2007-08-30
What application?
What have you done to try install it?
In what way it is not working? Error-messages or what?

Info please!

---

### Post by rdoolen on 2007-08-30
Cool, I figured that this must option had to be someplace.

Thanks!

---

### Post by phibit on 2007-08-30
Just so others who read this thread are clear, if you try to install a program in Wine, and it tells you the version of Windows you're running is too ancient, do the following:

In console, run:
winecfg

This will bring up the wine cfg window. Look around, and in one of the tabs, there's a dropdown menu that lets you choose which version of windows to 'emulate' (I know, I know, Wine Is Not an Emulator...). Chances are you want to change this option to Windows XP (default is Windows 2000 i believe)

---

