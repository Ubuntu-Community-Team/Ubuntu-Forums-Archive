---
title: "[SOLVED] Menu items away, how?"
date: 2008-02-24
forum: General Help
---

### Post by Sera88 on 2008-02-24
I have a little problem with my Xubuntu 7.10 32-bit Linux: Today I installed Tomb Raider 2 onto the machine by mounting an image with this command.
```
 sudo mount -t iso9660 -o loop /media/disk/TombRaider2.img /mnt/iso
```

It installed fine and quickly also, but then it didn't work. Then I uninstalled the program from **Applications -> Wine -> Uninstall Wine Software**. Now I have in the menu **Applications -> Others** 8 entries of that game (e.g. "Core Design", "Setup Tomb Raider"...).

**So how can I remove those entries?**
I purged the Wine's installation directory ("C:\Program Files\Core Design\") and still no luck.

---

### Post by TeoBigusGeekus on 2008-02-24
[http://ubuntuforums.org/showthread.php?t=702476](http://ubuntuforums.org/showthread.php?t=702476)

---

### Post by Sera88 on 2008-02-24
I installed CCleaner and cleaned every possible thing it could find, but no luck. The menu items are still there.

---

### Post by TeoBigusGeekus on 2008-02-24
Right click Applications menu and select edit menus.
Go to Wine and uncheck or even remove all unnecessary entries.

---

### Post by soldats on 2008-02-24
the menu items are actually .desktop files normally located in /usr/share/applications/ if you wish you can remove them and it will remove them from the menu or a better way would be to make them backups. if you need more help with xfce please head to the xfce home page where most of your questions should be answered.

---

### Post by Sera88 on 2008-02-25
Actually I've tried modifying the Application menu editor, but it doesn't list the system's menu items (e.g. "Graphics", "System" and "Others"), so it's out of the question.
And I've also visited in the /usr/share/applications/ folder, and the items aren't listed there either. Not even as hidden files.

---

### Post by TeoBigusGeekus on 2008-02-26
Are you sure right clicking the applications' menu and selecting edit menus does not bring out a box with all your menu items?
At least that's how I dealt with the problem:
I used to delete the entries for the wine submenu and also delete the folders in wine's c:\program files folder but they kept coming back again. Since I installed and run CCleaner the wine application behaves the way *_**I**_* want it to behave (ok, almost... :))...

---

### Post by Yellow Pasque on 2008-02-26
> **Sera88 said:**
> Actually I've tried modifying the Application menu editor, but it doesn't list the system's menu items (e.g. "Graphics", "System" and "Others"), so it's out of the question.
And I've also visited in the /usr/share/applications/ folder, and the items aren't listed there either. Not even as hidden files.
How about in ~/.local/share/applications?
(Note: ~ =/home/<username> , make sure you're not root if you use this shortcut in terminal)

---

### Post by Sera88 on 2008-02-26
This is what I get after right-clicking the Applications menu and selecting "Edit menus":

[img]http://img337.imageshack.us/img337/7276/screenshotwt5.jpg[/img]

It's in Finnish.
*erotin* means "separator"
*sisällytys* means "contents"
*järjestelmä* means "system"

EDIT: Temüjin, that was it! It's now cleaned, and the menu items are away. I deleted the contents of ~/.local/share/applications/programs/Core Design/ and they were gone. Thanks a bunch.

---

### Post by Yellow Pasque on 2008-02-26
Go to the terminal
```
cd /home/sami/.local/share/applications
ls -la
```

---

