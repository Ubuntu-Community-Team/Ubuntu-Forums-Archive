---
title: "How to run wine doors??"
date: 2007-02-12
forum: General Help
---

### Post by tjtansey on 2007-02-12
I wanted to give wine-doors a try, as it looked from their web site to be easy to use, bit I'm very frustrated.  I followed the intructions for installation from "How to Wine", didn't work.  After hunting down the .py file, I then ran it and got a bunch of scrolling script.  I assumed the installation was progressing.  I then tried to run wine-doors and got the following msg:
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in ?
    import ui
  File "/usr/share/wine-doors/src/ui.py", line 39
    ui.window['progressbar'].set_fraction( percentage )licked( widget, data=None ):
                                                            ^
SyntaxError: invalid syntax
Does anyone have any insight on this?  I tried to find some help from the wine doors site, but I couldn't even find a link to submit a question.   Needless to say I'm a little dubious to the usability of this application.

---

### Post by tbroderick on 2007-02-12
[http://www.wine-doors.org/trac/ticket/416](http://www.wine-doors.org/trac/ticket/416)

---

### Post by tjtansey on 2007-02-12
Does that mean there is a fix to it?

---

### Post by tbroderick on 2007-02-12
No. That means there is a bug in the program.

---

### Post by tjtansey on 2007-02-12
I was afraid of that.  Oh well guess I stick with winetools

---

