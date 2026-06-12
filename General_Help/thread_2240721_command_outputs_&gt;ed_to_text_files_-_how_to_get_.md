---
title: "command outputs &gt;ed to text files - how to get readable wrapping and indentation"
date: 2014-08-21
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-08-21
I use pretty large fonts in terminal emulators and text editors. (In everything actually, but those two are relevant.)

With either lxterminal or xvt if I enter a command that produces lines of output longer than the window is wide most of them (not quite all) will be automatically wrapped and indented in a way that makes them easy to read.  But if I send the output to a text file with a ">" and open it with eview (vim for dummies) the "smart" wrapping and indentation that would have appeared in the terminal is replaced by eview's dumb wrapping and is much harder to read. If instead I open it with gedit, gedit complains of invalid characters.

I can pipe the command output through fold like```
man man | fold -s -w 40 > delme.txt
``` it improves things slightly by setting what column to wrap on and limiting it to wrapping at spaces (i.e., not in the middle of a word) but the indentation still sux and it's still a lot harder to make sense of than the output of the same command in the terminal.  I've tried useing ```
lxterminal --geometry=40x40 -e man man > delme.txt
```but all I got was an empty file.

So how can I make bash send the output of commands as neatly wrapped and folded as lxterminal and xvt do to a text file? Is there some weird character lxterminal and xvt are using for a tab (indent) that I need to "tr" into something else to get it to display properly in a text file?

---

