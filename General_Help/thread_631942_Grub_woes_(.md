---
title: "Grub woes :("
date: 2007-12-05
forum: General Help
---

### Post by Hawk__0 on 2007-12-05
I used root (hd0,0) because my linux drive is on 0,0
and windows is on 1,0
so i do setup (hd0)
setup (hd1)
reboot and then both give error 17, cant mount or sometihng

:(
help?

---

### Post by oeolycus on 2007-12-05
In what order did you install Windows and Ubuntu?

Also, to my knowledge you should only have to type:

```
setup hd0
```

because you want to setup GRUB at the beginning of your first partition. Report back if any of this helps.

EDIT: you could also try [Super Grub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

---

