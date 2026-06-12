---
title: "permanently delete without shift"
date: 2008-01-14
forum: General Help
---

### Post by fetjesus on 2008-01-14
ok I gues this is a kde(konquerer) and gnome question.

Is it possible to have ubuntu and kubuntu not move things to the wastebin with the delete button? instantly perm delete like with shift delete? I hate the wastebin :)


Tried to search for this on the forum but I gues I am a bad looker :)

---

### Post by wout.wepsait.com on 2008-01-14
In a default installation of ubuntu, you can enable this option in nautilus. Nautilus is the filemanager gnome uses, gnome is the graphical user interface ubuntu uses.
 
Go to you home folder:
 
Top menu bar >> Places >> Home
 
Go to the preferences menu:
 
Edit >> Preferences
 
Click on the second tab, it's called Behavior
 
At the bottom you will see an option called "Include a Delete command that bypasses Trash". Check the checkbox in front of this line.
 
Click close.
 
 
If you right click on a file or folder you will have an extra option under "Move to Trash" called Delete.
 
This will perminantly delete the file/folder.

---

### Post by JackandJohn on 2008-01-30
Just a quick other note since I am mini-brainstorming: you might be able to link trash to /dev/null, which would have the effect of the system thinking it's moving the item to trash the normal way, but in fact it will be directing it to the system's black hole.

Note: I have not ever used it this way, it just makes sense that it would work, which is to say it's worth testing :)

From [http://en.wikipedia.org/wiki/Data_sink](http://en.wikipedia.org/wiki/Data_sink)
In Unix-like operating systems, /dev/null or the null device is a special file that discards all data written to it (but reports that the write operation succeeded), and provides no data to any process that reads from it (it returns EOF). In Unix programmer jargon, it may also be called the bit bucket or black hole.

---

