---
title: "edit text file with a command line function"
date: 2006-12-28
forum: General Help
---

### Post by Camden on 2006-12-28
I'm trying to figure out a command that will insert a line of text in a file (ex. xorg.conf).  I'm trying to put together a script that I can run after a fresh install that will automatically add a line  to my xorg.conf file.  I'm guessing I use the sed command.  But I have never used it before and can't seem to figure it out.  

The main thing is I don't want to use gedit.  I want to do it directly from command line.  Is it possible?

---

### Post by dcstar on 2006-12-28
> **Camden said:**
> I'm trying to figure out a command that will insert a line of text in a file (ex. xorg.conf).  I'm trying to put together a script that I can run after a fresh install that will automatically add a line  to my xorg.conf file.  I'm guessing I use the sed command.  But I have never used it before and can't seem to figure it out.  

The main thing is I don't want to use gedit.  I want to do it directly from command line.  Is it possible?

If you want to insert/change things in a file then the **sed** command is probably the one (but it can be "fun" to get sorted out......)

If you want to just add to the end of a file, then the **cat** command may be easier to work with.

---

### Post by Camden on 2006-12-28
Thanks for the info.  I'm somewhat succesfully using the sed command.  I've got it doing what I want but I probably couldn't tell you how I did it.

---

### Post by phatlip on 2006-12-28
vi <file>.conf

then type ":h" + "enter" (without quotes)

will give you a list of keys that do things, however you don't need to know everything. just press "i" to start editing and "esc" to stop and "shift"+"ZZ" to save.

---

