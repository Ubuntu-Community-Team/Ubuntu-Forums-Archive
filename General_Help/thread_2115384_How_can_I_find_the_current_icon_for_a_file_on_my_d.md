---
title: "How can I find the current icon for a file on my desktop?"
date: 2013-02-12
forum: General Help
---

### Post by ubername on 2013-02-12
I have a file on my desktop which I have picked a nice icon for, using right click > properties then clicking on the icon and selecting a new icon file (.png)

The problem is I did this a long time ago and cannot remember where the .png is or what it is called. Anyone know how I can find the name / location of this .png file?

Thanks

---

### Post by ubername on 2013-02-12
Of course, what would be really useful would be if, when you clicked on the icon to choose the new .png, the 'file picker' window opened with the current icon file / location selected.

---

### Post by Cheesemill on 2013-02-12
It should be somewhere in the /usr/share/icons directory.

---

### Post by ibjsb4 on 2013-02-12
Are you saying that the icon still exist on your desktop?  If so just go back to the change icon window and click on the icon and that will take you right to its location.

---

### Post by stinkeye on 2013-02-12
If it's a desktop configuration file, drag and drop it into a gedit window.

---

### Post by ubername on 2013-02-13
Right clicking on the file on the desktop, selecting properties, then clicking on the icon takes me to a file picker window which opens at 'recently used', not the .png - that is what I was trying to get at in my second post.

I have over 4,000 icons in usr/share/icons  - I was hoping that there was a way of identifying which one it was.

The file is in fact a script, so dropping it into gedit opens the script. 

There must be a setting somewhere (maybe a file attribute?) which tells the desktop how to display it (location, size, appearance etc.) It feels really 'unLinix' not to be able to get to it easily.

---

### Post by col48 on 2013-02-13
This doesn't provide an answer but it may provide a *little* insight.

I have some gambas executables for which I have devised my own icons, which live in .png files (nowhere near /usr/share).  Once I have associated the icon to the executable I can do anything I like to the original .png file including deleting it and it makes no difference to the icon shown against the executable.

Therefore I infer the way the association is handled is not as simple as one might think.  The icon is presumably not stored in the file as the 'date modified' is not changed when the icon is changed and in addition icons can be associated with plain text files which can be entirely human-readable.

This web page, found by internet search, is dated 2006 but it might just help:

[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)

However, I haven't verified that it still holds good, and it certainly doesn't work for the gambas programs of mine.

---

### Post by ubername on 2013-02-14
Thanks Col, that is very interesting, and a good insight regarding the ability to mess with the original png files to no effect once associated.

---

