---
title: "Easiest way to cut and paste from terminal to X?"
date: 2021-08-13
forum: General Help
---

### Post by dbee on 2021-08-13
I want to cut and paste from terminal/emacs to X applications.

What's the easiest method? i've had a look online and nothing works for me.

---

### Post by HermanAB on 2021-08-13
Highlight and middle click?

---

### Post by guiverc on 2021-08-13
I'd highlight & right-click  (*which offers a menu, and reminder of what keyboard shortcuts exist if you don't want to click*)

Providing specific OS, release, desktop (or WM) & terminal may also help; as Ctrl+INS works on some as well; but not my default terminal/desktop choice.

---

### Post by Impavidus on 2021-08-13
A terminal is a GUI application (in contrast to the applications running in the terminal). Copying and pasting works in the same way as in any other GUI application, except that the keyboard shortcuts use ctrl+shift+c, ctrl+shift+v, where other applications use ctrl+c, ctrl+v. Select and middle click works best (unless your middle mouse button is broken, as often happens for me).

---

### Post by TheFu on 2021-08-13
I use select & paste. It is part of X11 and has been for 35+ yrs. It uses the X-buffer.

[LIST=1]
[*]Select with the left mouse button - there are single, double, and triple-click techniques.
[*]Paste with the middle mouse button.
[/LIST]

No keyboard needed.
No menus needed.

select ... move to the input field, paste.
This is for text only.  For other complex copy/paste operations, use one of the clipboards.

In 21.04, I've noticed that bash changed their default settings to screw with proper pasting.  If I select the EOL, when I paste, I want the command to have an <enter> ... like it has for 35+ yrs.  If I select in a way that doesn't include an EOL, then the paste should reflect that as well and not run a command.

PuTTY from Windows, sorta does the select/paste method, just with the right-click to paste immediately. Or it did last time I used Putty - perhaps 10 yrs ago.

---

### Post by dbee on 2021-08-13
```

dara@laptop-20-04:~$ uname -a
Linux laptop-20-04 5.11.0-25-generic #27-Ubuntu SMP Fri Jul 9 23:06:29 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

Whenever I try to cut and paste from terminal the cut option is greyed out when i right-click with the touchpad. I've tried multiple files and I've done a 

```

sudo emacs -nw myfile.php

```

The cut option doesn't appear. Pls see attached screenshot...

[IMG]https://i.ibb.co/GvzQ2Bh/ubuntu-cut-and-paste.png[/IMG]

---

### Post by TheFu on 2021-08-13
There's no such thing as cut in a terminal using a mouse. Sorry.  Terminals are like paper. Once they are printed, line by line, there's no going back.  A terminal window isn't like a full-screen editor. It is only the last line that can be modified.  Learn your shell to understand how to do that.  Regardless of where you place the mouse and tell it to paste, it will only paste where the cursor is on-the-last-line.  That paste could be insert or overwrite - just depends on your shell settings.  Typically, people use either emacs or vi keybindings for their shell editor. That only means something if you know those two editors.

[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) shows how to perform command line editing with bash - among other things.  Read it once a year, so the things you don't understand today can still be learned next year when your understanding has expanded.

---

### Post by TheFu on 2021-08-13
BTW, if you are using emacs, perhaps you want to use Xemacs for cut/paste?

---

### Post by dbee on 2021-08-20
don't like X. speaking of which. 

i've uninstalled emacs-gtk 

but emacs is still on my desktop GUI. how do i remove all X emacs altogether?

---

### Post by TheFu on 2021-08-20
Search for  "Ubuntu Desktop Guide" or "The Linux Command Line". Both those references answer these sorts of questions.  

There might be a desktop guide for each different GUI, LXQt/LXDE/XFCE/Mate/KDE, but the default on is for Gnome3.  I don't use any of those. Sorry.  They all work basically the same, I'd assume.

---

