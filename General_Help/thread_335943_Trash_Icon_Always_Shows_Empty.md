---
title: "Trash Icon Always Shows Empty"
date: 2007-01-11
forum: General Help
---

### Post by zephyrus54 on 2007-01-11
My trash icon always appears as empty even when there is indeed trash.  Consequently, it won't let me empty my trash when I right click on the icon, and only when I open the trash window can I actually empty my trash.  This was not a problem before, and I just noticed this change today.

---

### Post by bruenig on 2007-01-11
Have you tried right clicking on the trash and selecting remove from panel, and then right clicking and adding it again?

---

### Post by RagingOcelot on 2007-01-20
Same problem.  And removing the applet and adding it didn't help.  Also tried restarting the panel...no help there, either.

---

### Post by PatrickPizinho on 2007-02-02
I have the same Problem, and I have also no idea how to handle it. But now you now you are not alone with this!

---

### Post by PatrickPizinho on 2007-02-03
Hi. Now my Trash can works perfect... what I did? nothing. I simply rebooted the system. Reboot systems seems to be a magic solution not only for windows, but for Linux too!

---

### Post by DerArzt on 2007-02-11
I still have the problem. Rebooting seems to have done nothing for me.

---

### Post by maestrobwh1 on 2007-02-14
I sometimes get crap I can't empty. It annoyes me, although I can just use a file manager in root mode and go to that folder.  You'll need to show hidden files: 
home/youruserid/.local/Share/Trash/files

I know with kubuntu, I assume a similar directory structure with ubuntu, my user trash is a different directory than my root trash. My root trash will be empty, but you need to go to home/youruserid/.local/Share/Trash/files (there is another directory next to /files in Trash there called "info" so I sometimes find I need to go in there and clean it out... although I generally need to reboot, or just toss a random file in trash (not from root!), to get the icon to show full or empty.

I use Thunar (sudo thunar) in root mode when I have such issues. It is nice and smiple. I like Krusader for KDE, but it is just too busy at times.  Just know, that if you delete when you are sudo/root, the files go in root Trash folder, rather than youruserid Trash.  I had done some work in root, and had over 100MB in junk there before I learned this.

If you are using a file manager in sudo <root> then check the permissions on youruserid folder.

---

### Post by hackle577 on 2007-05-03
I am having the same problem now with Feisty, but I think it has something to do with .Trash folders being created on external drives. From what I've read, a .Trash folder is created there that the trash applet points to, but when you eject the drive, it never points back to your regular trash directory.

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247)

---

### Post by hotani on 2007-05-18
Same here. I have a mysteriously empty trash can with stuff in it. The only way to empty it is to open the folder and manually delete the items.

---

### Post by FuturePilot on 2007-05-18
Hmmm, I see this bug from Edgy still exists:(

---

### Post by oce on 2008-01-18
same problem here with an up to date Gutsy
my ~/.Trash directory belongs to me and all files in it are from my local home directory but the Trash icon shows an empty trash and the "empty trash" command in the context menu is grayed
could it be a bug in the trash applet?

---

