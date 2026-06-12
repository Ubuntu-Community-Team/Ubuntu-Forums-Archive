---
title: "How can I reliably kill / restart XBMC in a way my mom can use?"
date: 2013-01-07
forum: General Help
---

### Post by AncientPC on 2013-01-07
I have a laptop running Ubuntu and XBMC for my parents can use. Occasionally, XBMC will freeze and they have no way of restarting XBMC. The desktop is unresponsive.

If this was on Windows, my parents would hit `ctrl-alt-del`, kill XBMC, and reopen it. If this was me, I'd drop into shell and run `pkill xbmc`.

I need a method my parents can use on Ubuntu. Restarting the laptop every time XBMC freezes is not an option.

I tried running `xkill`, but it complained that it can't grab cursor. I rebound Task Monitor to `ctrl-alt-del`, but it doesn't work when the system is locked up.

I'm open to any suggestions.

---

### Post by ibjsb4 on 2013-01-07
You say the desktop is unresponsive, but sounds like not totally.  Could you in terminal ..

```
killall xbmc && xbmc
```That assumes that xbmc is the proper command to start it.  And if the mouse will still work, turn that command into a button in the panel.

---

### Post by NooB Frank on 2013-04-06
I had the same issue in Xubuntu.  I found my answer here:  [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu]("https://sites.google.com/site/easylinuxtipsproject/first-xubuntu")   (<--- solution credit goes to this author.  His instructions pasted below for ease of use)

I think that this should work in Ubuntu just the same.

[INDENT]In a terminal enter: 
```
gksudo leafpad /etc/default/keyboard

```

Find the line:
XKBOPTIONS=""

Change that line to this: 
XKBOPTIONS="terminate:ctrl_alt_bksp"

Save the modified file and close it.

Reboot your computer.

After logging in again, you can test it: Ctrl+Alt+Backspace should reboot only the desktop and throw you back into the login window.
[/INDENT]

For me if XBMC hangs - now I can kill it by hitting Ctrl+Alt and Backspace.  Log back in and it brings me back to my desktop. 

Good luck!

Frank

---

