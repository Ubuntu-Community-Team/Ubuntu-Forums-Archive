---
title: "Problem in Lubuntu 14.04.1 with creating shortcut to folders on desktop"
date: 2015-01-11
forum: General Help
---

### Post by bartek6 on 2015-01-11
Hi everybody,

First I say about architecture of my PC. I've 3 hard drives.
Hard drive no 1 (120 GB) - only for Lubuntu 14.04.1
Hard drive no 2 (40 GB) - only for Windows 7 Professional SP1
Hard drive no 3 (250 GB) - common data file (pictures, movies, music etc.) for Lubuntu 14.04.1 and Windows 7 SP1

I want to have on Lubuntu desktop (Hard drive no 1) shortcut to folders from Hard drive no 3. I don't have any problem with creating this shortcuts. I used command
```
 ln -s xxx/yyy/zzz aaa/bbb/ccc 
```

This shortcuts work fine without problem till restart of the computer. After turnig on my PC my icon's of shortcurs are changed and after double-click folders aren't opened, but apears list of installed programs. Does anybody know how to solve this problem?

---

### Post by ajgreeny on 2015-01-11
It is probably easier to make three separate launchers/icons on the desktop for pcmanfm, if that is what you are using, and add the path to the folder in question for each launcher.

The launchers are actually simple text files called .desktop files which you can edit in leafpad/mousepad or whatever and edit the Exec line of each file to **Exec=pcmanfm /home/username/foldername** for each one appropriate to the folder you want to see. You will have to rename the files, for example, as **pcmanfm1.deskop**, **pcmanfm2.desktop**, as you can't have two same named files on the Desktop.

---

### Post by bartek6 on 2015-01-15
Could you explain me how to create it step by step? I've tried, but successless. :-(

---

