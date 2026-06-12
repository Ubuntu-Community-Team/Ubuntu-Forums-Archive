---
title: "How do you clear the recent files list in nautilus?"
date: 2013-06-15
forum: General Help
---

### Post by stinkeye on 2013-06-15
As the title says....
or better...how to remove the Recent item on left altogether.

---

### Post by howefield on 2013-06-15
Remove the file..

```
rm ~/.local/share/recently-used.xbel
```

---

### Post by stinkeye on 2013-06-15
> **howefield said:**
> Remove the file..

```
rm ~/.local/share/recently-used.xbel
```

That's what I thought but files remain in the recent view after running and then killing nautilus with....
```
nautilus -q
```

---

### Post by howefield on 2013-06-15
You might need a log out and log back in.

Never noticed your OP edit, not sure about removing the "Recent" label from Nautilus but you can permanently disable the feature. A quick google should sort that, I can't remember the detail.

---

### Post by stinkeye on 2013-06-15
Log out/in ...recent still there.
I know of solutions before of changing write permissions of the **~/.local/share/recently-used.xbel** file,
but the Recent in nautilus doesn't appear to use this file.
Deleting recent in Zeitgeist privacy doesn't work either.

---

### Post by mc4man on 2013-06-15
Best way to clear - 
open "Recent', select all > delete (either using the r.click > delte or shift+delete

Not sure you can remove "Recent" from sidebar easily but to stop nautilus from populating it - 
create a file - 
~/.config/gtk-3.0/settings.ini

add this to file - 
```
[Settings]
gtk-recent-files-max-age=0
```

(Unfortunately  that's the only value that has any effect (0). So it's all or nothing. Had upstream bug on how "Recent" is 'all & forever' instead of 'recent'  but they couldn't grasp the dofference. 
If gtk-recent-files-max-age=XX worked or gtk-recent-files-limit=XX worked then one could limit how long or how many entries are kept but they don't so it's all or none

---

### Post by stinkeye on 2013-06-15
> **mc4man said:**
> Best way to clear - 
open "Recent', select all > delete (either using the r.click > delte or shift+delete

Not sure you can remove "Recent" from sidebar easily but to stop nautilus from populating it - 
create a file - 
~/.config/gtk-3.0/settings.ini

add this to file - 
```
[Settings]
gtk-recent-files-max-age=0
```

(Unfortunately  that's the only value that has any effect (0). So it's all or nothing. Had upstream bug on how "Recent" is 'all & forever' instead of 'recent'  but they couldn't grasp the dofference. 
If gtk-recent-files-max-age=XX worked or gtk-recent-files-limit=XX worked then one could limit how long or how many entries are kept but they don't so it's all or none
Yep that works.Thanks.
I don't like the way, anything I open in smplayer, image viewer, gedit etc shows up in nautilus recent.
So even though I like to use recent in gedit, it's now off.
At least with the Dash recent, I can control what applications or files it logs.

I also fouind [**[COLOR="#B22222"]indicator-privacy[/COLOR]**]("http://www.florian-diesch.de/software/indicator-privacy/")
which has a menu item for "clear recent file list" which makes recent disappear immediately.

---

### Post by mc4man on 2013-06-15
removing recently-used.xbel would also work as previously mentioned, though "Recent" in nautilus will still show the previous until recently-used.xbel is re-created (by opening any file by any app that uses recently-used.xbel

Maybe the indicator option 'clears' the file rather than removing it?

---

### Post by stinkeye on 2013-06-18
I ended up leaving gtk-recent-files on
and made a quicklist item for nautilus with the **Exec=** line...
```
Exec=sh -c "echo > ~/.local/share/recently-used.xbel"
```
Clears recent immediately.

---

### Post by rtimai on 2013-11-06
FWIW after 4 months, this also works (in Terminal or TTY1) without having to install anything:

**> ~/.local/share/recently-used.xbel && ls -l ~/.local/share/recently-used.xbel**

The second command after && lists the file to verify it is 0 bytes.

Next time, simply use up-arrow in Terminal to re-select the command from the BASH history. To edit out unwanted BASH history entries:
**gedit ~/.bash_history**

---

### Post by Alex22 on 2014-05-02
Hi Guys,

I am driving Ubuntu 14.04 and erasing recently-used.xbel method didn't work for me.
Settings.ini method as well (they say it doesn't work with nautilus 3.8 and higher).

What worked is :

dconf-editor
go to org->gnome->desktop->privacy 
and uncheck the remember-recent-files 

[http://askubuntu.com/questions/294901/how-to-disable-recent-files-folder-in-nautilus](http://askubuntu.com/questions/294901/how-to-disable-recent-files-folder-in-nautilus)
(ionash'es answer)

---

