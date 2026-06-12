---
title: "Help with removing a program installed with WINE"
date: 2007-02-04
forum: General Help
---

### Post by zazen666 on 2007-02-04
Hi, 
I installed a game using wine, didint work, and now want to uninstall. There does not seem to be an unistall option for it, and i cant find it with the synaptice package manager. Do I need to use a command from the terminal? which one?
thanks so much

---

### Post by dcstar on 2007-02-04
> **zazen666 said:**
> Hi, 
I installed a game using wine, didint work, and now want to uninstall. There does not seem to be an unistall option for it, and i cant find it with the synaptice package manager. Do I need to use a command from the terminal? which one?
thanks so much

Synaptic knows nothing about things under Wine, you have to either find the Windows uninstaller that came with the software, or find the "winetools" utility that (IIRC) can uninstall these things.

---

### Post by mgmiller on 2007-02-04
If it was installed as a windows game under wine, it was installed to your .wine directory.  In Nautilus, open your home directory and hit ctrl h to show all the hidden directories, then find .wine and open it.  inside it navigate to drive_c and then to windows.  In there you will find a file called uninstall.exe.  double click it to run it and you should see a list of all the windows programs that wine has installed.  The rest is just to select the one you want and click uninstall.

Good Luck.

---

### Post by zazen666 on 2007-02-04
that last one did it, thanks a lot guys

---

