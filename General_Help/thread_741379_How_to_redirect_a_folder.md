---
title: "How to redirect a folder?"
date: 2008-03-31
forum: General Help
---

### Post by MountainX on 2008-03-31
I am thinking about using Tomboy to store stuff that should be encrypted. I would like to make Tomboy store all its data on a mounted encrypted partition. Since Tomboy doesn't seem to offer any config options, is there a way I can make the default Tomboy folder (/home/user/.tomboy) point to another location?

I'm guessing that I might copy the folder contents, then delete the entire folder, then create a link to the new encrypted folder and put the original contents there. Will this work? If so, would I just use 
```
ln -s /media/encrypted /home/user/.tomboy
```

Or would I use a hard link?

---

### Post by Oldsoldier2003 on 2008-04-02
> **MountainX said:**
> I am thinking about using Tomboy to store stuff that should be encrypted. I would like to make Tomboy store all its data on a mounted encrypted partition. Since Tomboy doesn't seem to offer any config options, is there a way I can make the default Tomboy folder (/home/user/.tomboy) point to another location?

I'm guessing that I might copy the folder contents, then delete the entire folder, then create a link to the new encrypted folder and put the original contents there. Will this work? If so, would I just use 
```
ln -s /media/encrypted /home/user/.tomboy
```

Or would I use a hard link?

in theory it should work. I would be prepared to restore it to the original configuration just in case tomboy freaks out.

also I would use ln -fs instead of ln -s

---

### Post by MountainX on 2008-04-02
> **Oldsoldier2003 said:**
> in theory it should work. I would be prepared to restore it to the original configuration just in case tomboy freaks out.

also I would use ln -fs instead of ln -s

Thank you.
  -f, --force                 remove existing destination files

---

