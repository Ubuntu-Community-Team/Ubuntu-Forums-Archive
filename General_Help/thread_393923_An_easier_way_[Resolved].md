---
title: "An easier way? [Resolved]"
date: 2007-03-26
forum: General Help
---

### Post by cisforcojo on 2007-03-26
Hey guys,

I am trying to run a Windows program and add an icon for it to my (GNOME) desktop.
When I run the program in a terminal, I ALWAYS have to type:
XMODIFIERS=""    (or anything in wine will hang)


then run the program:
wine /path-to-file -winver winxp

I made a script to handle this and then created a "Launcher Icon".
I changed the file permissions: chmod +x script.sh

Now when I dbl-click on the icon, it asks if I want to open the text file or run it.
Obviously I want to be able to skip this step. How can I make this easier?

Is there a way in just the URL: part of the Launcher Icon I can run: XMODIFIERS="" and then "wine /path-to-file......."?

Thanks for the help!!!

---

### Post by aysiu on 2007-03-26
I believe there's a setting in Nautilus (the file manager) preferences to always execute instead of asking you what you want to do with scripts.

Go to Places > Home > Edit > Preferences and dig around.

---

### Post by zvacet on 2007-03-26
Why do you run terminal when you have icon on desktop?Another way is
```
winefile
```
find your program exe(probably in C>program files) and double click on it.

---

### Post by cisforcojo on 2007-03-26
Ah I didn't make that clear enough. I don't WANT to run from the terminal, I was just illustrating what I currently do it make it work.  I want to only use the icon. I'll look into winefile and the Nautilus settings

---

### Post by Lord Illidan on 2007-03-26
I'd just save the script, then make a new launcher through the desktop normally, and in the COMMAND part, enter the name of the script.

---

### Post by zvacet on 2007-03-27
Maybe you can do that this way.download exe in any folder(let´s say programs for this time).
Type in terminal
**wine /home/username/programs/your exe**
That should create icon on your desktop and you can just click on it

---

### Post by cisforcojo on 2007-03-27
Lord Illidan: 
That's what I've done. I've created a script and called it from the launcher icon. Maybe I wasn't clear about that. When I double click the icon, a window pops up asking if I want to display the file or run it (since it's a text file with executable permissions). I'm trying to skip this step and JUST get it to run it.



About wine /home/username/program/program.exe, this doesn't make an icon on the desktop.
The other problem with that is, I have to type XMODIFIERS="" in the terminal first, otherwise wine will hang. I can't just call 'wine program.exe'. I need to call XMODIFIERS="" first.

---

### Post by aysiu on 2007-03-27
> **cisforcojo said:**
> When I double click the icon, a window pops up asking if I want to display the file or run it (since it's a text file with executable permissions). I'm trying to skip this step and JUST get it to run it. And this is a preference in Nautilus. Did you try it yet?

---

### Post by cisforcojo on 2007-03-27
That works perfectly! Thanks for your help!

---

