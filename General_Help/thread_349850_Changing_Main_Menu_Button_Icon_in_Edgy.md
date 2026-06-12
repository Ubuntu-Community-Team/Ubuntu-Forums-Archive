---
title: "Changing Main Menu Button Icon in Edgy"
date: 2007-01-30
forum: General Help
---

### Post by bg1256 on 2007-01-30
Just as the title says.

I found these directions for Dapper on gnome-look:

> How to change a menu button (tested in Ubuntu Dapper):
1. add a main menu applet to your panel
2. run gconf-editor
3. go to /apps/panel/objects/object_1
4. check use custom icon
5. in custom icon key add an image path

For some reason, I can't get this to work on Edgy.  Just curious if anyone has any ideas about this.

---

### Post by NiceGuyUK on 2007-01-31
The object_1 bit changes from machine to machine - on mine (was Edgy, now Feisty, but same location), its at apps/panel/objects/object_0

Quick way to tell is to look at the "Object type" field on the same gconf screen - if it says "menu-object", you've found the right one!

---

### Post by bg1256 on 2007-01-31
Yeah, I discovered that it's object_8 on my machine, but I can't change the icon for some reason.

---

