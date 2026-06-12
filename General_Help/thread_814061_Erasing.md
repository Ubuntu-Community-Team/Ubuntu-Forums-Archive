---
title: "Erasing?"
date: 2008-05-31
forum: General Help
---

### Post by ur0b0r0 on 2008-05-31
So i had frets on fire but i wanted to erase all songs, i enter as root in usr/share/games/data with nautilus and then i erased the songs folder because i needed some free space,cause i only got 120 mbs left and the fof songs are more than a 2 or 3 gbs,anyway i delete it but it doesnt even go to the trash or anything it just dissapeared from that folder without making free space or anything it just doesnt appear to be there but it is still there because i erased it as root and now i still have 120 mbs but the folder is gone.. i did some tests creating folders and pasting stuff on them ,erasing them again but they dissapear too! i dont get it , they just go without leaving free space.:confused::confused::confused:

---

### Post by quelx on 2008-05-31
since you did it as root maybe it's in the root trash folder

Open a terminal and type

```
sudo ls -lah /root/.Trash/
```

---

### Post by Zeenomorph on 2008-05-31
That is a strange situation.  They may be going to the hidden folder that Frets is using.  Try hitting ctrl + h to view hidden files and then doing a search for that folder name.  You may be able to find where it is going that way.

---

