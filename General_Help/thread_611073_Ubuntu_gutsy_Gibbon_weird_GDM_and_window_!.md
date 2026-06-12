---
title: "Ubuntu gutsy Gibbon weird GDM and window !"
date: 2007-11-12
forum: General Help
---

### Post by szadek_ on 2007-11-12
Hello everybody .I think i found a bug on this version ( 7.10 ) .It seems that the login page , GDM , has a bug with the font used on the login , the chareters are too big , i only see part of them , and the password also the font is big.Another problem is with the windows , the border where the minimize , maximize and close are placed , the are big aswell , so i think this is a bug .I downloaded 3 times the live cd , all them have this problem , even with live session , the windows borders are too big , and ugly .I serched on the forums for possible similar problems and i didnt found anything .Anybody knows how to solve this ? or a update to solve this ?! ...

---

### Post by por100pre1 on 2007-11-12
If the GDM resolution is different, yes it is a bug. Try setting up your video card and monitor settings manually: Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
gksu displayconfig-gtk
```

---

