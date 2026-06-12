---
title: "Premission"
date: 2005-09-04
forum: General Help
---

### Post by wytzehoekstra on 2005-09-04
Hello Iv a problem with setting my permissions.
Iv got 3 partions;
2 X Fat32
1X Ext3

If I open Gparted all the partitions are locked which means I can't do anything.
In the permission tab of the properties the strange thing is that it says  I can't change the settings because im not the owner. However under owner it says im the owner.

With the EXT3 i can change every permission but not with the fat32.
It's not possible to do anything with both of them in gparted.

Does anyone know how this could be solved?

---

### Post by wytzehoekstra on 2005-09-04
Maybe someone can tell me how the user & group settings work I don't understand the purpose of group ... well atleast the options presented have very stang names like games video etc...u would expect it to be names of forinstance group 1 which cantain user A, B, etc...

oke hopefully someone can help me

---

### Post by wytzehoekstra on 2005-09-04
anybody?

---

### Post by kosmic on 2005-09-04
start Gparted with the sudo comand :

sudo gparted, now you can change your partitions

---

### Post by arnieboy on 2005-09-04
[QUOTE=wytzehoekstra]Hello Iv a problem with setting my permissions.
Iv got 3 partions;
2 X Fat32
1X Ext3

If I open Gparted all the partitions are locked which means I can't do anything.
In the permission tab of the properties the strange thing is that it says  I can't change the settings because im not the owner. However under owner it says im the owner.

With the EXT3 i can change every permission but not with the fat32.
It's not possible to do anything with both of them in gparted.

Does anyone know how this could be solved?[/QUOTE]
right click on the fat32 partition and click "unmount". then u can do whatever u want to do with it.

---

### Post by arnieboy on 2005-09-04
[QUOTE=kosmic]start Gparted with the sudo comand :

sudo gparted, now you can change your partitions[/QUOTE]
gparted starts in sudo mode already

---

