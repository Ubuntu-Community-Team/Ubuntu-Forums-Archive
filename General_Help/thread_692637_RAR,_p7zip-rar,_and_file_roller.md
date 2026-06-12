---
title: "RAR, p7zip-rar, and file roller"
date: 2008-02-10
forum: General Help
---

### Post by BattlePanic on 2008-02-10
There is a package called p7zip-rar which allows the 7z compression tool extract rar files.  I installed this and it seems to work from the command line but GNOME's file roller still will not recognize rar files.  Is there a way to tell file roller to use the 7z command to extract rar files?

---

### Post by dcstar on 2008-02-10
> **BattlePanic said:**
> There is a package called p7zip-rar which allows the 7z compression tool extract rar files.  I installed this and it seems to work from the command line but GNOME's file roller still will not recognize rar files.  Is there a way to tell file roller to use the 7z command to extract rar files?

Synaptic-Search-"unrar"

---

### Post by zvacet on 2008-02-10
```
sudo apt-get install rar unrar p7zip p7zip-full
```

Right click on rar file and select **unpack here**.

---

### Post by BattlePanic on 2008-02-10
thanks for the tips everyone.

It sounds like File Roller is only capable of handling rar files by using the unrar package.  Out of curiosity, does anyone know if File Roller can use the functionality provided by the p7zip-rar package to to handle rar extraction?

---

### Post by swotie on 2008-03-13
Thanks for the code

sudo apt-get install rar unrar p7zip p7zip-full

It works very well

---

