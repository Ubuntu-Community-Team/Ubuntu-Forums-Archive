---
title: "Permission Problems and Trash"
date: 2008-04-14
forum: General Help
---

### Post by Antispaceman on 2008-04-14
Using Ubuntu 8.04

I can delete a folder cause I don't have the permission
Normally I would run sudo nautilus and delete it from the .trash folder but I can't find it now

How do I delete it?

---

### Post by sisco311 on 2008-04-14
```
sudo rm -fr ~/.local/share/Trash/files/*
```
in hardy the trash is in ~/.local/share/Trash/files/

---

