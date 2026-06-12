---
title: "Noobie, how to set permissions?"
date: 2007-07-29
forum: General Help
---

### Post by manicmario on 2007-07-29
In order to fix my sound problem i got this code
mkdir /usr/src/alsa
   cp downloaddir/alsa* /usr/src/alsa

So i made the directories in the terminal, but now i have to copy the downloads to that file, not through the terminal but by drag and drop. But this wont let me, says i have no permission to write to the folder.

I have been into the "Users and Groups" section and put myself as admin, and checked all the boxes in privilages.

Please help me, i'm really new at this .

Thanx

---

### Post by s6dalane on 2007-07-29
Type *gksudo nautilus* into the terminal and after inserting your password, a nautilus window pops up, where you will have root rights to move/modify files.

---

### Post by rillip on 2007-07-29
The above works around the issue, but it's easily fixed.

Right click on the folder and go to properties after you've launched nautilus as the super user as described above.  Righ click and go to properties (I think, not 100% familiar with Nautilus's layout). Change teh ownership to your username that you login with instead of root.

Or from a command line run

```
sudo chown youruser foldername
```

---

