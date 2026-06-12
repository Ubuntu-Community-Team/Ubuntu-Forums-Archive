---
title: "[SOLVED] how to remove a windows program?"
date: 2007-10-14
forum: General Help
---

### Post by RuB3N on 2007-10-14
I installed a MS program. But I cant get it off now. in my panel its in applications<wine><programs><ventrilo><ventrilo    

But i dont know how to get rid of it.







thanks for your time:)

---

### Post by por100pre1 on 2007-10-14
Check if you can find an uninstaller for that program in the WINE Uninstaller:

```
uninstaller
```

---

### Post by RuB3N on 2007-10-14
i tried the uninstaller and the program is still there when i uninstalled it

---

### Post by bengar on 2007-10-17
Saludos x100pre
I have the same problem. i run the uninstaller then it does not be removed. Do you know other way to uninstall it?
Thank in advanced
bengar

---

### Post by quibbler on 2007-10-17
If you installed the MS program with wine, and then uninstalled it with wine, then it should be gone.
In your file browser make sure you can see hidden files and folders, then look in your home directory in 

/home/your home/.wine/drive_c/Program Files/

and check to see if your program is Not there. If it is, you can just delete the files and folders.

As for the wine menu item in the start menu. You can get rid of this by going to

/home/your home/.config/menus/applications-merged/

and delete the wine menu item you no longer want.

quibbler

---

### Post by bengar on 2007-10-17
quibbler
Thank you very much, This worked, now is clear.
Bengar

---

### Post by elgalloloco on 2007-10-21
> **quibbler said:**
> If you installed the MS program with wine, and then uninstalled it with wine, then it should be gone.
In your file browser make sure you can see hidden files and folders, then look in your home directory in 

/home/your home/.wine/drive_c/Program Files/

and check to see if your program is Not there. If it is, you can just delete the files and folders.

As for the wine menu item in the start menu. You can get rid of this by going to

/home/your home/.config/menus/applications-merged/

and delete the wine menu item you no longer want.

quibbler

Thank you so much for this!!!!

---

