---
title: "my desktop isn't showing any of the files"
date: 2007-09-07
forum: General Help
---

### Post by sarahsilverman on 2007-09-07
only if i log out and back in it shows up, but when i start the computer no files show up. i don't know how this happened.

thanks any help is greatly appreciated :popcorn:

**************************************************************************************SOLVED***************************************************************************************************************

---

### Post by banewman on 2007-09-07
Which files do you have on the desktop that aren't showing? Do you mean the icons for file system, trash and other op systems - or are they files that you placed there yourself?

---

### Post by sarahsilverman on 2007-09-08
> **banewman said:**
> Which files do you have on the desktop that aren't showing? Do you mean the icons for file system, trash and other op systems - or are they files that you placed there yourself?

only the desktop files, all of them aren't there. you can't right click it either. the files do show up in the (i don't know what you call it in linux) explorer window.

---

### Post by banewman on 2007-09-08
Sorry, I don't know what you are calling desktop files. When I see my desktop I have icons for the computer, trash and my other mounted filesystems. There are .desktop files that are normally hidden. Is that what you mean? They are config files.

---

### Post by sarahsilverman on 2007-09-09
> **banewman said:**
> Sorry, I don't know what you are calling desktop files. When I see my desktop I have icons for the computer, trash and my other mounted filesystems. There are .desktop files that are normally hidden. Is that what you mean? They are config files.

sorry no again, nothing shows up

here : [http://img50.imageshack.us/my.php?image=somethingua6.png](http://img50.imageshack.us/my.php?image=somethingua6.png)

thank you very much for helping me :popcorn:

---

### Post by ansi on 2007-09-09
> **sarahsilverman said:**
> sorry no again, nothing shows up

here : [http://img50.imageshack.us/my.php?image=somethingua6.png](http://img50.imageshack.us/my.php?image=somethingua6.png)

thank you very much for helping me :popcorn:

Do I understand you correctly: after your first login to the system you don't see any icon on your desktop, but when you make logout and do repeated login you see icons on the desktop?

Please, show us an output of the following command execution:
```
ls -la ~/Desktop
```

---

### Post by eggdeng on 2007-09-09
Is this gen? This is not a desktop but a wallpaper opened in Image Viewer. Right-click on the Chocolate.jpg icon on the bottom panel to get a close option. The Desktop will be behind the wallpaper.

---

### Post by jocko on 2007-09-09
It could be that nautilus by some reason is set not to show the desktop.
Try this:
Start up gconf-editor (press Alt+F2, type "gconf-editor" and enter).
In gconf-editor, browse to /apps/nautilus/preferences/
Look for the key "show_desktop" and make sure it is enabled.

---

### Post by prodigal on 2007-09-09
If you're really really new to Linux I would recommend using Kubuntu rather than Ubuntu, they've done SUCH a GREAT job of making it like windows. You can do almost everything you can do in windows and just as easily. Should be almost completely un-necessary to use the command line. (Which was one of the aims of the Kubuntu project so well done folks :D)

---

### Post by sarahsilverman on 2007-09-09
> **ansi said:**
> Do I understand you correctly: after your first login to the system you don't see any icon on your desktop, but when you make logout and do repeated login you see icons on the desktop?

Please, show us an output of the following command execution:
```
ls -la ~/Desktop
```

total 9575564
drwxr-xr-x  5 jonathan jonathan       4096 2007-09-09 17:02 .
drwxr-xr-x 56 jonathan jonathan       4096 2007-09-09 16:51 ..
drwxr-xr-x 11 jonathan jonathan       4096 2007-09-09 17:02 Backup Folder
-rw-r--r--  1 jonathan jonathan 5091142628 2007-09-09 16:25 Backup Folder2.tar.gz
-rw-r--r--  1 jonathan jonathan     127488 2007-09-05 18:07 BlankMap2007.png.ppt
-rw-r--r--  1 jonathan jonathan        109 2007-07-23 22:39 .directory
-rw-rw-rw-  1 jonathan jonathan        121 2007-09-09 17:02 Filesystem.desktop
-rw-r--r--  1 jonathan jonathan 4698675200 2007-08-08 20:47 .fr.6486.0.JaS.Mac.OS.X.10.4.8.AMD.Intel.SSE2.SSE3.PPF.1.Defiant.diskutil.biker880.ich7-R.patch.Integrated.tar
drwxr-xr-x  8 root     root           4096 2007-07-29 21:52 jre1.6.0_02
drwxr-sr-x 11 root     root           4096 2007-08-23 18:13 RealPlayer
-rwxr-xr-x  1 jonathan jonathan    5790356 2007-08-23 18:11 RealPlayer10GOLD.bin

---

### Post by sarahsilverman on 2007-09-09
> **eggdeng said:**
> Is this gen? This is not a desktop but a wallpaper opened in Image Viewer. Right-click on the Chocolate.jpg icon on the bottom panel to get a close option. The Desktop will be behind the wallpaper.

sorry this isn't the case, its kind of silly i was searching chocolate on the net. thanks for putting in that idea anyway. i went and checked, but it wasn't an image viewer.

---

### Post by sarahsilverman on 2007-09-09
> **jocko said:**
> It could be that nautilus by some reason is set not to show the desktop.
Try this:
Start up gconf-editor (press Alt+F2, type "gconf-editor" and enter).
In gconf-editor, browse to /apps/nautilus/preferences/
Look for the key "show_desktop" and make sure it is enabled.

sorry, i checked and the box is selected. thanks anyway.

---

### Post by sarahsilverman on 2007-09-09
> **prodigal said:**
> If you're really really new to Linux I would recommend using Kubuntu rather than Ubuntu, they've done SUCH a GREAT job of making it like windows. You can do almost everything you can do in windows and just as easily. Should be almost completely un-necessary to use the command line. (Which was one of the aims of the Kubuntu project so well done folks :D)

hmm, i did try kubuntu but i like the things that ubuntu can do. doesn't kubuntu have desktop effects and can i change the theme of kubuntu?

---

### Post by kangol69 on 2007-09-10
I'm having the same problem.

---

### Post by sarahsilverman on 2007-09-10
> **kangol69 said:**
> I'm having the same problem.

my problem is solved, i think it had something to do with compiz. it wasn't working, then when i updated everything it worked again.

thanks everyone for all your help :popcorn:

:guitar:

---

