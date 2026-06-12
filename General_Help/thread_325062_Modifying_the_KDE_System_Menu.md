---
title: "Modifying the KDE System Menu"
date: 2006-12-24
forum: General Help
---

### Post by srunni on 2006-12-24
Hi,

Does anyone know how to edit the KDE System Menu? I'm not talking about the KMenu, but the little button next to it, which you can click on to open different folders in Konqueror.

Thanks in advance for the help!!!!

---

### Post by PacShady on 2006-12-28
Doubt you'll have any luck. Seems not a single person on this forum or the Kubuntu one have any clue on how to change this menu. I've got a problem that was probably caused when I upgraded to the latest KDE and now instead of being sent to "media:/" I'm being sent to "/media" like Edgy. Not a single person seems to know how to fix it yet, and Edgy has had the same problem since it was released months ago.

'Shady

---

### Post by PacShady on 2006-12-28
OK, after several hours of Googling I managed to find the solution.

Seems the directory you need is /usr/share/apps/systemview. This is how to fix that nasty problem in Edgy where the "Storage Media" in the System Menu points to /media instead of media:/ (edit the media.desktop file). Hope this helps you, and all the others who have had trouble with this part of KDE.

'Shady

---

### Post by srunni on 2006-12-30
Well, I actually prefer /media to media:/, especially in the OOo "Save As" sidebar, because using the KDE "media:/" means that there are various problems, such as thumbnails not showing up in Konqueror, and not being able to save in OOo without switching to /media. I will try out your tip for the System Menu though, because I haven't upgraded to Edgy yet (will probably go straight to Feisty) and I hate the "media:/" thing that is in Dapper, while I also want to add entries to System Menu for things like my music, apps, and videos folders.

---

### Post by PacShady on 2006-12-30
Well yeah, you can also use it if you prefer the /media over media:/ by editing the same file. It's up the top of the file, the current line should read under Dapper "Path=media:/", just change it to point to /media instead.

You should also be able to add items to the System Menu by throwing .desktop files into this directory too. I've considered adding a link to / in this menu, as well as a link to Konqueror in SuperUser mode.

'Shady

---

### Post by Gomek on 2007-04-08
Been looking for this for a while.  Thanks!

---

### Post by hikaricore on 2007-04-08
Awesome, now I can finally add drives to this and have them stay put.  :)

---

### Post by Trail on 2008-02-04
Thanks a lot :)

---

