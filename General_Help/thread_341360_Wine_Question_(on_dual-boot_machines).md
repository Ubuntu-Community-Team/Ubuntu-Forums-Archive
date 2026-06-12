---
title: "Wine Question (on dual-boot machines)"
date: 2007-01-18
forum: General Help
---

### Post by Forge42 on 2007-01-18
A rookie WINE question:

I have a dual boot machine right now with Edgy and XP living side by side.  I recently bought Half Life 2 and I wanna get it up and running.

My question:

From within Edgy, I can see my Windows partition and the associated files.  So, can I just point Wine at those files and run them from within Edgy?  Or do I have to actually go through the install process twice if I want to run it in both OSs?

I guess the short version of my question is:  Is wine capable of running programs that are resident on a seperate actual Windows partition/installation?

Thanks!

---

### Post by Stemp on 2007-01-18
> **Forge42 said:**
> Is wine capable of running programs that are resident on a seperate actual Windows partition/installation?

Yes

---

### Post by Forge42 on 2007-01-18
Any particular syntax or risks I need to be aware of?

Or do I basically just cd to the appropriate folder in a terminal and run:

```
wine appname.exe
```

and cross my fingers?

---

### Post by Stemp on 2007-01-18
Just cd into the appropriate folder and wine app.exe ;) (don't forget to use winecfg before)

---

### Post by AusIV4 on 2007-01-18
> **Stemp said:**
> Just cd into the appropriate folder and wine app.exe ;) (don't forget to use winecfg before)
I would question this method. If the appropriate folder is NTFS (read only), and the application tries to write something in its current directory, wouldn't you have problems?

---

### Post by Forge42 on 2007-01-18
FWIW, I have the NTFS-3g driver installed.

What do you mean about winecfg?  What do I need to be sure to do with it?

---

### Post by Stemp on 2007-01-18
> I would question this method. If the appropriate folder is NTFS (read only), and the application tries to write something in its current directory, wouldn't you have problems?

> What do you mean about winecfg? What do I need to be sure to do with it?

This is linked.. if you start the command winecfg it'll create a .wine/etc... folder
By example  your save folder will be created in your home ;)

---

### Post by DoktorSeven on 2007-01-18
Only thing you need to be aware of is that some programs will install support libraries, files, etc. on your Windows filesystem in other places than the install directory.  In this case you would have to install these programs again to place the proper support files in ~/.wine/drive_c (your WIndows C drive in Wine).

Generally these just crash with a DLL not found (or similar) error.

---

