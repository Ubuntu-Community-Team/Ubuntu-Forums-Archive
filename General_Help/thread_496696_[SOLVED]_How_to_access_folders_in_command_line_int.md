---
title: "[SOLVED] How to access folders in command line interface with spaces in folders name"
date: 2007-07-09
forum: General Help
---

### Post by philidox on 2007-07-09
I know this sounds stupid but I have been googling left and right and I cannot figure out how to access folders in the cli with spaces in the name.  For example like if a folder is name "data.file", all I have to do is type cd data.file and then i'm in the directory but if the folder is name "data file" and I type cd data file it will give the error stating that folder or directory does not exists.  PLEASE tell me how!!!

---

### Post by Ozor Mox on 2007-07-09
I think you have to surround it with quotes, like

```
cd "data file"
```

---

### Post by Trebaruna on 2007-07-09
Alternately, use a backspace before the space: that way the command line treats it as a space in a name, instead of thinking you've moved on.

i.e. /media/data1/My\ Stuff

---

### Post by vanadium on 2007-07-09
Single quotes can also be used. What you also should learn, is to use command line completion. If you type for example

ls dat<tab>

(pres the tab-key after typing part of the file name)

then the file name will be completed if it is the only one that matches: the result will be:

ls data\ file

This saves you typing and reduced the chance of typing errors.

---

### Post by philidox on 2007-07-09
THANK YOU!!!, I have been struggling on how to do that for months.

---

### Post by marsbt on 2007-07-09
> **philidox said:**
> THANK YOU!!!, I have been struggling on how to do that for months.
you should have posted here earlier then ;)
Enjoy.

---

### Post by az on 2007-07-09
A wonderful console file manager is Midnight Commander

sudo apt-get install mc

Hit F9 and enable lynx-like motion and you are good to go.  It really speeds up certain tasks when you are at the CLI.  F10 gets you out of the menu.  F3 to view a file, F4 to edit.  F8 to delete....

---

### Post by philidox on 2007-12-07
> **az said:**
> A wonderful console file manager is Midnight Commander

sudo apt-get install mc

Hit F9 and enable lynx-like motion and you are good to go.  It really speeds up certain tasks when you are at the CLI.  F10 gets you out of the menu.  F3 to view a file, F4 to edit.  F8 to delete....

I like mc that was nice!

---

