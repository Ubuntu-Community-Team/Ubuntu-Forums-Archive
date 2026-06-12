---
title: "uninstalling application from wine"
date: 2008-05-30
forum: General Help
---

### Post by armandli on 2008-05-30
I'm running into some problem uninstalling programs from the wine emulator. I know that if you delete wine from your OS, it would be gone with it, but I prefer not to do that.

Instead, I did several things: 

1. went to .wine/drive_c folder, deleted the application from the program files folder
2. went to .wine/drive_c/windows folder, found all files that is related to the name of my application, and deleted them, including some item that is in the start menu folder in windows

now i went to the Wine menu in ubuntu Application applet, the application i just deleted is still showing in the installed programs menu. i restarted my computer, and the name is still there.

I didn't try clicking on those items yet, but previously i have already used the uninstallation program for the application and it didn't work. 

so my question is: how do i manually edit the program menu in wine and delete the application's menu items?

---

### Post by WRDN on 2008-05-30
Try removing any entries corresponding to the software you wish to/ have removed in:

Applications > Wine > Uninstall Wine Software

---

### Post by armandli on 2008-05-30
I have already tried that. the software is no longer present in the uninstall software menu

---

### Post by armandli on 2008-05-30
okay.. not all of the items in the uninstalling program in wine dissapeared. my program is Autodesk Maya 8.5. there uesd to be three items listed in the uninstall program: maya direct connect, maya, and maya documentation. but now after what i did, only direct connect shows up. 

funny thing is, after i deleted the files in /home/<my username>/.wine/drive_c/windows/profiles/<my username>/Start Menu/Programs and then i click on uninstall the direct connect, the files that once represents the menu items of Maya appears again, all of them

---

### Post by armandli on 2008-05-30
nvm. i fixed my problem. all the menu items .wine has is saved in .local/share/applications/wine

---

