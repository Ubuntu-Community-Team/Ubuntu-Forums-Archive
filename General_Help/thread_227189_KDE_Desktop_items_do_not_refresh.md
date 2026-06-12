---
title: "KDE Desktop items do not refresh"
date: 2006-08-01
forum: General Help
---

### Post by charafantah on 2006-08-01
i have Kubuntu dapper 6.06 running on several machines

when a user saves a file on his dekstop, the icon for the file will not appear on desktop, even when i hit refresh manually(from the menubar)

though, if i open konqueror and navigate to ~/Desktop/  the file exist there with no problem....

why is that happening?and how do i fix it?


regards

---

### Post by Jucato on 2006-08-01
Just to check:

Right-click on the desktop and choose Configure Desktop. Go to Behavior, and check if "Allow icons on desktop" is enabled. If it is, check in the File Icons tab if that particular file type is enabled.

---

### Post by charafantah on 2006-08-01
yes it is

i forgot to mention that if you logout/login the items will appear normally,

---

### Post by Bigglez on 2006-08-16
Yeah - this super sucks. It used to do this on Fedora Core 3 KDE as well.
I find if you right-click and add a new document (say a text file) - suddenly the icons will be redrawn. 
Of course, this is not a solution. I don't know what is.

---

### Post by eprparadocs on 2007-03-19
The trick to getting KDE to refresh its desktop is to execute the command:

dcop kwin KWinInterface refresh

That'll do it.

C.

---

### Post by Pikestaff on 2007-03-19
I've been having this problem too recently... thanks for the trick.  But do I have to do it anytime I want to refresh the desktop?

---

### Post by Bigglez on 2007-03-19
*makes a note* :D

---

### Post by taisao on 2008-06-19
I still having this problem with ubuntu hardy/8.04 & kde 3.5.9 .

dcop kwin KWinInterface refresh doesn't work for me but 
```
dcop kdesktop KDesktopIface setIconsEnabled false && dcop kdesktop KDesktopIface setIconsEnabled true
``` work (a little slow)

One can make a kde menu item for it and assign a shortcut for that menu item. 	:idea:

---

