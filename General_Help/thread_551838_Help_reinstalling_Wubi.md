---
title: "Help reinstalling Wubi"
date: 2007-09-15
forum: General Help
---

### Post by rodolfosrg on 2007-09-15
:mad:A week ago I had to uninstall wubi. When doing so a message appeared in the lower right corner of the screen that said that C:/wubi/disks/system virtual disk was damaged and requested to execute CHKDSK. I ran the chkdsk and It did something but i didnt know what was it.The ubuntu boot loader dissapeared and everything was fine until I discovered that in the add/remove programs, wubi was still there and when I ran wubi installer it loaded as if uninstalling wubi.In the wubi directory the system.virtual.disk can not be deleted,renamed, moved, anything.:confused::confused::confused:
Now I need to re install ubuntu but I cant because it tries to uninstall it.
can someone help me with this please?.
Thanks 8-[

---

### Post by ago on 2007-09-17
Delete the folder manually, then delete the key 

HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

