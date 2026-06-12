---
title: "Deleting the &quot;Examples&quot; folder in Home Folder"
date: 2015-01-24
forum: General Help
---

### Post by michael-piziak on 2015-01-24
I thought I'd delete the "Examples" folder in the home folder of 12.04 lts

I'm curious though.  Where exactly is that folder - in the home folder it appears to be a link to the real folder.  I think I would only be deleting the link and not the folder also by trashing "Examples"

?

---

### Post by mc4man on 2015-01-24
It's a link to folder holding 2 example a/v files in /usr/share/example-content/Ubuntu_Free_Culture_Showcase

---

### Post by deadflowr on 2015-01-24
try
```
unlink examples.desktop
```
assuming you haven't moved out of the default home folder location when you open a terminal.
otherwise use the full path /home/you/examples.desktop

---

### Post by michael-piziak on 2015-01-24
I'm attempting to navigate to the actual folder with the GUI
I'm in Home folder and viewed the hidden folders, but I don't see any of the folder names mentioned by either of you

?

---

### Post by deadflowr on 2015-01-24
It shows as Examples in Home Folder(nautilus), but shows as examples.desktop in a terminal.
(run the ls command and you'll see an entry for examples.desktop.)

When you click on Examples it'll route you to the usr/share/example-content directory.
(If you click on it look up at the top pane where it would say something like HOME[ it's a button]; it should be right above the main window area, I don't know what to call it.
But after clicking on Examples that top pane should now show usr share example-content Ubuntu _Free _Culture_Showcase)

Anyway if using the Home Folder instead of a terminal, move to trash should do what you want.
I'm pretty sure it won't regenerate.

I'm not sure if i made any sense or not.

---

### Post by michael-piziak on 2015-01-24
Thanks so much - I understand now !

One other question:  I was experimenting and deleted the folder in Home folder that links to that.   What if I want to put the link back - I don't see where you can create a link in the directory by right clicking the folder.

---

### Post by Holger_Gehrke on 2015-01-24
> **michael-piziak said:**
> I thought I'd delete the "Examples" folder in the home folder of 12.04 lts

I'm curious though.  Where exactly is that folder - in the home folder it appears to be a link to the real folder.  I think I would only be deleting the link and not the folder also by trashing "Examples"

?

What you see on your desktop is a .desktop file - that's a bit more than **just** a link. If you open a terminal and enter
```

less Desktop/examples.desktop

```
you'll see how much more ... (use the 'q' key to exit less).

I would advise against removing the files and the directory linked to with the file manager or with the shell, because they are installed through the package manager system and there's some other stuff connected to it that's strewn all around the file system. A copy of the .desktop file is in /etc/skel -- a directory whose content get's copied to the home directory of any new user that gets created. And there's several dozen translation files for the desktop file in all the language directories of /usr/share/locale. The right way to remove it is to find out what package installed it and -- if it doesn't provide anything else that you might want to keep -- remove the whole package.

To find out what package the file belongs to, do
```

dpkg-query -S example-content.desktop

```

This should tell you, that the file belongs to the package 'example-content'.

To see what else is in that package, do
```

dpkg-query -l example-content.

```

If you still want to get rid of it, do
```

sudo apt-get remove example-content

```

---

### Post by deadflowr on 2015-01-24
It's a link .desktop file and not an application .desktop file, ftr.

---

