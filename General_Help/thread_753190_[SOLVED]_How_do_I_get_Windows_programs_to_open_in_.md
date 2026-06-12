---
title: "[SOLVED] How do I get Windows programs to open in WINE?"
date: 2008-04-12
forum: General Help
---

### Post by emotionlovesyou on 2008-04-12
I want all my .php files to open in Dreamweaver via WINE

I assume your right-click on the PHP file and select Properties then the Open-With tab, but I don't know know how to format the open-with command.

:guitar:

---

### Post by HermanAB on 2008-04-12
Basically, you have to change directory to where the Windows program is, then launch wine with the name of the exe file as a parameter.  Once you got it figured out, you can make an application launch thingy or put it in a menu.

Something like:
cd /where/ever/it/is;wine whatever.exe

Cheers,

Herman

---

### Post by bingoUV on 2008-04-12
Have you installed Dreamweaver in wine? If you open it, does Dreamweaver start all right? If yes
    Do you know where your Dreamweaver exe file is located? Just select that exe as the executable in the open-with. If all goes well, and the wine service is running, Dreamweaver should start.

---

### Post by emotionlovesyou on 2008-04-12
> **bingoUV said:**
> Have you installed Dreamweaver in wine? If you open it, does Dreamweaver start all right? If yes
    Do you know where your Dreamweaver exe file is located? Just select that exe as the executable in the open-with. If all goes well, and the wine service is running, Dreamweaver should start.

So this is the custom command for Open With?

```
/home/emotion/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe
```

It says: Could not find...

---

### Post by mc4man on 2008-04-12
If there is a space in path use '.......'```
wine '/home/emotion/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe'
```

always start with wine<space> in any case
above is terminal command
if using right click open with> custom command just insert /usr/bin/wine

---

### Post by emotionlovesyou on 2008-04-12
> **mc4man said:**
> If there is a space in path use '.......'```
wine '/home/emotion/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8/Dreamweaver.exe'
```

always start with wine<space> in any case
above is terminal command
if using right click open with> custom command just insert /usr/bin/wine

You're a flippin' genius!!! Thanks a bunch.

:KS:KS:KS

---

