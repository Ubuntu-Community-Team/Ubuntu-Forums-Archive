---
title: "Scite Question"
date: 2008-01-22
forum: General Help
---

### Post by mabryant on 2008-01-22
I have two questions that I can't seem to find an answer using my google-fu skills.  

I have installed Scite and, coming from a Notepad++ user, really like it.  The one thing I can't seem to make it do is to open new files in the same window under a new tab. When using Notepad++ in Windows when I double click on a new file, it opens in a new tab, however, Scite opens a new window.  Is there a command line switch I need to do in order to do this?

The other question is the automatic saving of what files are open so the next time you open Scite it opens the same files.  

Has anyone figured out how to do this yet?

Thanks,

Mark

---

### Post by diaa on 2008-01-25
> **mabryant said:**
> I have installed Scite and, coming from a Notepad++ user, really like it.  The one thing I can't seem to make it do is to open new files in the same window under a new tab. When using Notepad++ in Windows when I double click on a new file, it opens in a new tab, however, Scite opens a new window.  Is there a command line switch I need to do in order to do this?

I know the answer for this part, Scite has something called *Options* file(aka *Configuration* file), which contains options in a simple scripting language called Lua.
There are several *Options* files, one per-system(for the whole PC) aka Global Options File, editable by  root only, another for each user, overrides settings in the per-system file, and a third per-folder, I think it also overrides per-user file.
You need to edit your per-user file to enable single instance(so it opens new files in new tabs in the same instance), to do this open scite, from the menu *Options* > *Open User Options File*, then add the following
```
check.if.already.open=1
```Since you were a Notepad++ user, I guess you'll be happy to know about the rest of my options file, here it is, commented(comments start with #):
```
# for formatting of source code
tabsize=4
indent.size=4

# one instance of SciTE only
check.if.already.open=1

# remove trailing whitespaces
strip.trailing.spaces=0

# max number of tabs
buffers=20

# reload file and prompt on activation(useful if file is modified by an external program)
load.on.activate=1
# prompt me for any suspicous action
are.you.sure.on.reload=1
# Show the statusbar, it contains useful information
statusbar.visible=1
```Another tip: to know what options are available you can[LIST=1]
[*]Have a peek at the global options file, it contains a lot of commented lines telling you about the defaults.
[*][Read the manual]("http://scintilla.sourceforge.net/SciTEDoc.html")[/LIST]-- 
Diaa Sami

---

### Post by mabryant on 2008-01-29
Thank you.  I swear I searched through the documentation, but must have missed it.

Again, many thanks.

Mark

---

