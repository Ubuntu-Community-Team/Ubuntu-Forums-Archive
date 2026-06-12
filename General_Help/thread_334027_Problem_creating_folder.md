---
title: "Problem creating folder"
date: 2007-01-08
forum: General Help
---

### Post by tc101 on 2007-01-08
I am using the Nautilus 2.16.1 file browser.   Under some folders I am able to create new folders, but under others I can not.  For example I can create a folder under tmp but not under usr.  I know I need to read more about the file structure of linux to understand how this works.  Can someone point me at a page that explains this.

---

### Post by tito2502 on 2007-01-08
/usr is a restricted directory. Only root can access it.

If you want to do it, the best way is to type

sudo mkdir /usr/dirname
into a shell.

Or, you could press alt + f2

in the command box type

gksudo nautilus

Enter your rot password and you should be able to make the directory.

Note: Don't use nautilus in sudo for everyday use.

---

