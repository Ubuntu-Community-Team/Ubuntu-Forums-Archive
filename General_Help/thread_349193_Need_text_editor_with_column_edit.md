---
title: "Need text editor with column edit"
date: 2007-01-29
forum: General Help
---

### Post by nuggetz on 2007-01-29
Is there a text editor that allows you to insert text in columns? Not sure if anyone has used Ultraedit for windows, but it comes in handy when trying to write things on multiple lines and it has the ability to edit your text in blocks or at the column level. Anyone know of such an editor for Linux?

Thanks

---

### Post by dcstar on 2007-01-29
> **nuggetz said:**
> Is there a text editor that allows you to insert text in columns? Not sure if anyone has used Ultraedit for windows, but it comes in handy when trying to write things on multiple lines and it has the ability to edit your text in blocks or at the column level. Anyone know of such an editor for Linux?

Thanks

You can achieve such things with the **sed** command, but it requires a fair learning curve.

---

### Post by nuggetz on 2007-01-30
I tried ultraedit under wine but it's horrible. The column mode doesn't work right. Maybe I'm using the wrong font. Anyone know of a good fixed width font under ubuntu??

---

### Post by biovore on 2007-02-12
Yeah, I been looking for one for a while.  ultra edit on windows is a GUI wrapping Emacs. (Sorta)  Cream for linux has a column editor mode, but it seems it only half work.  I am thinking of writing a QT Widget to do this on KDE.  I am amazed more people haven't noticed this gapping hole..  This is almost a requirement when working with VHDL.

Then again.. most of the people writting this stuff are java/c++/perl/python folks who don't really have a need for this feature.

---

### Post by g3k0 on 2007-02-12
try ed.  *cough*

---

### Post by justanick on 2007-02-26
Kate has basic column mode editing (Edit/Block Selection Mode). Works pretty well.

---

### Post by fsando on 2007-03-03
> **justanick said:**
> Kate has basic column mode editing (Edit/Block Selection Mode). Works pretty well.Does it?
To me it looks as if it only has block selection/block insert. How do you set it to edit in block-mode? That is, writing the same characters on multiple lines simultaneously.

---

### Post by justanick on 2007-03-04
> **fsando said:**
> Does it?
To me it looks as if it only has block selection/block insert. How do you set it to edit in block-mode? That is, writing the same characters on multiple lines simultaneously.
Well, you are right. You can't do that directly, it's *only* cut/copy/paste. That's why I wrote "basic column mode editing". Sorry if this was confusing.

Lame workaround: 
1. Write a line of characters you wish to insert on a single row (e.g. below your target text).
2. Duplicate this row to match the number of rows in your target text.
3. Cut & Paste into desired position in your target text.

---

### Post by fragos on 2007-03-04
Sounds like a lot of effort when wysiwyg packages like openoffice, abiword and scribus are available.

---

### Post by stylishpants on 2007-03-05
Vim does this very well. 

Hit [FONT="Fixedsys"]Ctrl-V[/FONT] and use motion commands to select a column of text, then use one of these commands:

[INDENT][FONT="Fixedsys"]I [/FONT]to enter insert mode and insert whatever you type next at the beginning of each row in the column  (or A to insert at the end of the column you selected)[/INDENT]

[INDENT]
    [FONT="Fixedsys"]s [/FONT]to replace each line in the entire with the text you type [/INDENT]

[INDENT]    [FONT="Fixedsys"]d[/FONT] or [FONT="Fixedsys"]x[/FONT]  to just delete the column[/INDENT]



[FONT="Fixedsys"]:help Ctrl-V[/FONT] for more information.

---

### Post by fsando on 2007-03-10
> **fragos said:**
> Sounds like a lot of effort when wysiwyg packages like openoffice, abiword and scribus are available.Sorry?
I think you misunderstand the needs expressed here.
We need a convenient way to handle pure text, typically for various scripting languages. We very often need to repeat many lines with only minor changes - and no DO WHILE etc. constructs will not work - that's why we need this feature.

By the way take a look at crimson editor at [http://crimsoneditor.com/]("http://crimsoneditor.com/")
I haven't tested but it may be better in wine than ultraedit it seems simpler.

---

### Post by fsando on 2007-03-10
> **biovore said:**
> I am thinking of writing a QT Widget to do this on KDE.  I am amazed more people haven't noticed this gapping hole..  This is almost a requirement when working with VHDL.
If you've got the skills, what about a plugin for an editor like bluefish?

Actually I'm thinking it could be possible - with a concerted effort to petition one of the editor-teams to implement this.
It may be something that is quite difficult to implement (or it may be some licensing issue?) because I only know two editors that has this: ultraedit and crimson editor ([crimsoneditor.com]("http://crimsoneditor.com"))

---

### Post by fragos on 2007-03-10
Prior to both Linux and wysiwyg on PC's the Wordstar editor had the feature you want.  When I did my diagramming with monospaced character graphics it was very handy.  I can see where copying in line code from and to areas with different indenting could benefit from block cuts.   Block cuts is what they used to be called to differentiate them from multicolumn page layouts like used in newspapers.  My personal approach to repetitive blocks of code is to write functions.  There can be many ways to solve the same problem.

---

### Post by fsando on 2007-03-11
> **fragos said:**
> Prior to both Linux and wysiwyg on PC's the Wordstar editor had the feature you want.Sounds interesting - I'm going to look in to this.

> **fragos said:**
> My personal approach to repetitive blocks of code is to write functions.This won't work in some scripting languages, in others it may work but is very inconvenient.
In addition: once you are getting used to that feature it seems so obvious it should be standard in any coding editor.

EDIT:
There is an interesting discussion here [http://bugs.kde.org/show_bug.cgi?id=56935]("http://bugs.kde.org/show_bug.cgi?id=56935") of whether the feature should enter into KDE's Kate. It seems developers don't care much for it - so we should probably stick with a windows app that will run nicely in a win-emulator for the future.

---

### Post by fragos on 2007-03-11
> **fsando said:**
> Sounds interesting - I'm going to look in to this.

This won't work in some scripting languages, in others it may work but is very inconvenient.
In addition: once you are getting used to that feature it seems so obvious it should be standard in any coding editor.

You are correct that the use of functions depends on the language.  No single tool solves all problems.

---

### Post by fsando on 2007-03-12
I believe there's hope:
[This]("https://bugs.eclipse.org/bugs/show_bug.cgi?id=19771") thread is about column edit in Eclipse and it appears that it is such a common feature in the competition that it is also finding its way into Eclipse - despite some mild resistance from the developers ;D
I've just downloaded an Eclipse plugin [columns4eclipse]("http://sourceforge.net/projects/columns4eclipse"), though, not tested yet (must learn to use Eclipse)

---

### Post by biovore on 2007-04-08
You all know that kate on kde has this function..  Its call block edit mode.  It behaves just like ultra edit on windows.

---

### Post by fsando on 2007-04-29
I just found a plugin for gedit that does something like that too - it's not all that ultraedit is yet but it's written in python and could probably be improved.
[http://live.gnome.org/Gedit/Plugins/ColumnMode](http://live.gnome.org/Gedit/Plugins/ColumnMode)
UPDATE:
> **biovore said:**
> You all know that kate on kde has this function..  Its call block edit mode.  It behaves just like ultra edit on windows.
I've just tested kate - it is not quite the same as ultraedit. ultraedit will let you select a column (0 or more characters wide) and let you write or delete on all lines simultaneously
I'd say that the plugin for gedit is more like ultraedit, though still some way to go.

---

