---
title: "[SOLVED] Photoshop wont budge"
date: 2008-03-19
forum: General Help
---

### Post by coninsan on 2008-03-19
Hi

Some time ago i installed photoshop cs2 on my pc via Wine, but now i wish to remove it and wine again, but when i run the uninstall process via wines program removal tool i wont remove.
i removed Winrar without a glitch but when it comes to photoshop and its apps, it wont budge, the programs stay put.
Anyone got an idea of how to get it removed? :)

---

### Post by danwood76 on 2008-03-19
When you say the programs stay put are the programs actually there or just the shortcuts to them?

---

### Post by coninsan on 2008-03-19
They stay as being fully functional.

---

### Post by danwood76 on 2008-03-19
manually delete them then.
locate them in your wine C: and delete all the files and then their shortcuts.
It will probs leave stuff in your wine registry but it wont effect ubuntu and will free up the deskspace.

The GIMP is just as good as photoshop for anything a home user would want to do.
Photoshop is a bit overbloated for you average user anyway.

---

### Post by coninsan on 2008-03-19
Photoshop is essential for my education along with illustrator, ive tried gimp but it just wont do, the same with blender for 3D but we havnt got that far just yet. 

Ill try to remove them manually and se how it goes. :)

---

### Post by danwood76 on 2008-03-19
Ah I see.
Are you running CS3 then under WINE?

---

### Post by coninsan on 2008-03-19
nope ive tried but it wont work, ill se if i cant get it to work under virtualbox, technically with a full copy of windows on my pc i should be able to run cs3 photoshop and illustrator. so i cross my fingers for it to work. 

The manual remove worked a treat but how do i get the entries to disapear, cous' when i remove wine the shortcuts stay in place. it would be perfect to get those to go away to

---

### Post by danwood76 on 2008-03-19
Do you mean in the gnome menu?

If you install alacarte
```

sudo apt-get install alacarte

```
you can then right click the apps menu, select edit menus and delete what you dont want.

---

### Post by coninsan on 2008-03-19
sweet thanks, this should also get rid of a few false entries in my menus thanks a million :-D

---

