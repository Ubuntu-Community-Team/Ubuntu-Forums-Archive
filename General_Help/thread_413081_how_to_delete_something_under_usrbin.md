---
title: "how to delete something under /usr/bin"
date: 2007-04-18
forum: General Help
---

### Post by Ioky on 2007-04-18
I have Install a online game call PlaneShift but however that game for some reason it can't run on my machine  So I use the uninstaller that come with it to delete the game, however there are three file under system:/media/sda2/usr/bin can't be remove, so I try to do it manually but it say "access denied to (where the file locate)" So how can I get them remove? and if some one know hot to get that game work, can you also tell me?

Thanks

---

### Post by dcstar on 2007-04-18
> **Ioky said:**
> I have Install a online game call PlaneShift but however that game for some reason it can't run on my machine  So I use the uninstaller that come with it to delete the game, however there are three file under system:/media/sda2/usr/bin can't be remove, so I try to do it manually but it say "access denied to (where the file locate)" So how can I get them remove? and if some one know hot to get that game work, can you also tell me?

Thanks

In a terminal:
```
cd /media/sda2/usr/bin
sudo rm *filenames*
```

And make sure you don't delete any important files by mistake!

---

### Post by RedSquirrel on 2007-04-18
You might want to remove them (perhaps one at a time) with:

```
sudo rm **-i** <filename>
```

The "-i" stands for "interactive" meaning you will be asked before the files are removed (in case you make a typo).

---

