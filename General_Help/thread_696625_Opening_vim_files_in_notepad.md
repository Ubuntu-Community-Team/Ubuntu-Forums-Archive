---
title: "Opening vim files in notepad"
date: 2008-02-14
forum: General Help
---

### Post by article on 2008-02-14
I really like vim a lot. However, I have run into a situation where csv files created in vim will not work with another program (BAT for Cisco Callmanager). When I open the vim csv file that I have created in Notepad, the breaks/carriage returns are replaced by squares. If I use Notepad to delete the squares, put the the breaks/carriage returns back in, and resave the file, BAT does not have any trouble importing the file. I have been trying to figure out what the essential difference is, and how to get vim to produce notepad-compatibile files, but I am at a loss. Any advice?

---

### Post by sammm on 2008-02-14
to change the file format to windows (dos):
:set ff=dos
to change the file format to linux/unix:
:set ff=unix
to check the file format:
:set ff

---

### Post by LaRoza on 2008-02-14
See [http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

Notepad on Windows is one of the few that uses CR/LF, most (all?) Unix systems don't.

Most editors that you can get for Windows don't have problems. 

I use [http://www.crimsoneditor.com/](http://www.crimsoneditor.com/) on Windows, and if you want a notepad replacement, you can use [http://www.notepad2.com/](http://www.notepad2.com/)

---

### Post by andrewjoy on 2008-02-14
This is one of the better text editors for windows imo

Notepad++
[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

to good thing is that it has add ons so you can well add on what you need :P.

---

