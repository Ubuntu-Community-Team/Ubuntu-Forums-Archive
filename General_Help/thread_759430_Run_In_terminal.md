---
title: "Run In terminal"
date: 2008-04-19
forum: General Help
---

### Post by Canuckelhead on 2008-04-19
I usually launch my python scripts from the terminal.

Sometimes it's just plain faster to run them from the GUI and select "Run in terminal" ... thing is I'd like to print some info for debugging purposes and the window closes once the script completes... or sometimes when it *doesn't* complete.  Any suggestions on how to keep the terminal window open after I run a script?

---

### Post by Rocket2DMn on 2008-04-19
Well, you can open a terminal normally: Application->Accessories->Terminal and run the script from there.  Then the terminal won't close.

---

### Post by Canuckelhead on 2008-04-19
I know that.  I usually do that.  But sometimes I get lazy and just want to double click 'em!

I'm sure there is a way to keep the terminal open!

---

### Post by Rocket2DMn on 2008-04-19
Hehe, I expected you knew that, but I've learned never to assume anything around here.  AFAIK, just using the right click function, there is no way to keep the terminal alive.  It certainly would be nice if you could right click and say Open Terminal here, I think Konqueror does that in KDE.  One option is to edit your scripts to not actually end until you tell them to, like finish it with an standard input request (so it can't complete until you click enter).
An alternative is to make a script in your home directory that changes directories to your scripts (or even runs them, too), then you can just pop open a terminal and run
```
source shell_script.sh
```
I always put a link to a terminal in a panel for quick access, too.

---

### Post by Canuckelhead on 2008-04-19
Yeah I rekon I'll just ask for some dummy input or something and it aught to stay up.  Unless I have bad code...  then it kills regardless...  No problem then.  Just have to 1)  Ask for some input before ending the script 2) Write better code!

---

### Post by ezak on 2008-04-19
Technically, there's not much need for scripts to simply keep the terminal open after a command finishes.

Easier solution, type the command you want, and then add "&" (without quotes) to the end.

Or half as easy, hit Alt + F2 and run all your commands from there. :)

---

### Post by bingoUV on 2008-04-19
Which terminal are you using? gnome-terminal has an option to not close when the issued command exits. 
Edit -> Current Profile -> Title And Command -> When command exits

mrxvt does it by default.
No idea about konsole.

---

