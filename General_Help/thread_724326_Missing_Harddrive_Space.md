---
title: "Missing Harddrive Space"
date: 2008-03-14
forum: General Help
---

### Post by jfordwashere on 2008-03-14
Hello,

For some reason I appear to be missing a bunch of harddrive space. I have a 52.7 gb harddrive (or there abouts). Using disk analyzer I see that 43.1 gb is used by my home directory. Yet when I try to see where it is used, disk analyzer shows three large directories (8.2 gb for .Virtualbox, and 6.6 gb for my "saved" directory", and 1 gb for my desktop). The rest of the directories cannot account for the missing 27 gb (please see attached image). Anyone have any ideas? (I ran fsck for the heck of it... didn't do anything)

Thanks,
-jack

---

### Post by scragar on 2008-03-14
graphic explain it all pretty much, starting from the middle you have the full drive(complete grey circle), the next ring out is almost completely /home inside that is almost completely /home/jford

now, inside that you have some folders, so the red one is virtual box, that's about 20%, then you have a hidden folder called saved, that's about 15%, and a smaller folder with your desktop in, and some more folders. the entire section without folders in is files. So files of some sort are accounting for about 45% of your HD by the looks of it.

---

### Post by forestpixie on 2008-03-14
got any hidden files in trash ?

---

### Post by jfordwashere on 2008-03-14
Cool thanks, (somehow) I got a really_really_really big file in my home directory.

---

### Post by scragar on 2008-03-14
```
ls -l -h -S ~/
```list's contents of your home folder largest first

ls = list
-l  = long, show info like filesize etc.
-h = human readable numbers, so k = 1024b, M = 1024k...
-S = sort ob size.
~/ = home dir.


very handy if you ever need to check things like that.

---

