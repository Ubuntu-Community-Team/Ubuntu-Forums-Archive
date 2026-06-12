---
title: "Trash on desktop?"
date: 2007-01-03
forum: General Help
---

### Post by rctxtreme on 2007-01-03
I have Ubuntu Edgy, is it possible to put trash on desktop? I've done heavy customisation to make myself feel at home with Linux, and adding the trash icon to the desktop will be better than squishing the single panel even more.

---

### Post by tronica on 2007-01-03
open gconf-editor and find /apps/nautilus/desktop, and check what icons you want to add.

---

### Post by qamelian on 2007-01-03
> **rctxtreme said:**
> I have Ubuntu Edgy, is it possible to put trash on desktop? I've done heavy customisation to make myself feel at home with a new distro, and adding the trash icon to the desktop will be better than squishing the single panel even more.

Press alt-F2 to get the Run Application box and type gconf-editor in the command line. Press enter and gconf-editor will run.

In the left-hand tree view, drill down to /apps/nautilus/desktop. Click on desktop to select it. In the right-hand view, put a check mark in trash_icon_visible. Close gconf-editor and you will now have a Trash icon on the desktop.

---

### Post by rctxtreme on 2007-01-03
Cool, thanks. *renames to Recycle Bin*

---

### Post by ubuntu27 on 2007-01-03
> **rctxtreme said:**
> Cool, thanks. *renames to Recycle Bin*

LOL. Recycle Bin

---

### Post by rctxtreme on 2007-01-04
I just got Kubuntu installed, so is there a way to do it on Kubuntu too? (i want to compare gnome and kde for one more time before i stay with one permanently)

---

### Post by obsidion on 2007-01-04
> **rctxtreme said:**
> I just got Kubuntu installed, so is there a way to do it on Kubuntu too? (i want to compare gnome and kde for one more time before i stay with one permanently)

 Add trash icon to your desktop

1. Right click on the desktop
2. Select "Create New > Link to Location (URL)..."
3. On the KDesktop dialog, enter:
1. File name: trash
2. Enter link to location (URL): trash:/
4. Click on OK

And to change the icon when the trash is empty:

1. Open a konsole
2. Write: echo "EmptyIcon=trashcan_empty" >> ~/Desktop/trash.desktop
3. Check if the file looks like in Trash trash.desktop example file.

---

### Post by rctxtreme on 2007-01-04
Finally, what do I do to make an icon have the image of the home button? And add a computer shortcut + it's image? Once that's done, this desktop issue is resolved :)

---

### Post by obsidion on 2007-01-04
> **rctxtreme said:**
> Finally, what do I do to make an icon have the image of the home button? And add a computer shortcut + it's image? Once that's done, this desktop issue is resolved :)

Right click on desktop...link to url set it to your home...set the icon

---

### Post by rctxtreme on 2007-01-04
Yeah, and when I used gedit to check it out:

```
Icon = unknown
```

---

### Post by obsidion on 2007-01-04
> **rctxtreme said:**
> Yeah, and when I used gedit to check it out:

```
Icon = unknown
```

  Well that lost me what are you on about ?

Right click on the icon that has been created, if you followed my above instructions, properties and set the icon to one of your choice. The conventional home icons are under filetypes

---

