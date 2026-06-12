---
title: "Re-installing WINE Completely (Including Settings)?"
date: 2008-06-21
forum: General Help
---

### Post by ivansf92 on 2008-06-21
Is there a way to remove everything that has to do with WINE and re-install it?

I'm asking this because, even though I deleted the .wine folder in my home folder and removed wine, when I re-install it, the settings remain.

Also, I deleted the Applications > Wine folder and when I re-install it, it does not re-create one.

---

### Post by jjk7288 on 2008-06-21
sudo apt-get remove --purge wine

---

### Post by drs305 on 2008-06-21
You can run a search to see what wine hits come up:
```
sudo find / -iname wine*
```

On my machine, these are the results. I would not have thought to look at a couple of these:
```

/home/username/.local/share/applications/wine
/var/lib/binfmts/wine
/usr/lib32/wine
/usr/lib/mime/packages/wine
/usr/bin/wine...
/usr/share/doc/wine
/usr/share/binfmts/wine
/usr/share/wine
/usr/share/applications/wine...
/usr/share/python-support/guidance-backends/winewrite.py


```

---

### Post by ivansf92 on 2008-06-21
Is there a way to delete the folders/files that come up, because for my computer, there are quite a few folders/files that came up, and it would be a lot easier if I could delete them using a command in the terminal.

---

### Post by drs305 on 2008-06-21
There is but I hesitate writing it as the one I would make would find any file/folder with 'wine' in it and I'm not comfortable enough that every file/folder with wine should be deleted (although it probably would be).

How about this, to limit the results. This would include only folders, which would probably produce results that you could delete with 'gksudo nautilus'.

```
sudo find / -type d -iname wine*
```

Then run the first find command and see how many files are still left ;-)

---

### Post by ivansf92 on 2008-06-21
Hmm...

The settings and stuff are all reset, but the Applications > Wine folder is still missing... And when I run winecfg using alt+f2, there is no icon that appears to the left of the command like it use to have when I first installed it.

---

### Post by drs305 on 2008-06-21
Did you reinstall wine? If so, I would try to uninstall it again since your first attempt probably left all sorts of pieces scattered around your computer. If you installed it via synaptic, and even if you didn't, I would try uninstalling it from there if at all possible. If it's not showing installed in synaptic, try installing and then uninstalling it (complete removal) to try to get rid of all remnants.

---

### Post by parhyang on 2008-07-01
'm using 8.04, I install wine 0.9x+Gogle SketchUp (free) it's working properly except in ruby script. next i try install IntelliCAD, then its become trouble at all, my wine goes slow down. for run notepad it will be 2-3minutes wait. so I uninstall SU and CAD then wine, but ./wine still exist, i'm ignoring and try to reinstall wine+SU but for now is not with others (CAD). but it's not works at all ... some body have experienced, knows and solved like these problems.?? please help me, i really need SU like my 1st run :(




:) thanks all, i remove manually. and reinstall wine, now its work. create launch, done..

---

