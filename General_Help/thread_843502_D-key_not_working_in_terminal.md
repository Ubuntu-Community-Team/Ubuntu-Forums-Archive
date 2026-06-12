---
title: "D-key not working in terminal"
date: 2008-06-28
forum: General Help
---

### Post by Aukikco on 2008-06-28
I have no idea of the cause, but I installed Xubuntu onto a friend's computer, and everything seemed to be working at first. However, during the second day of using, the d key stopped working in Terminal. When I start Terminal up, if I hit the d button before it has fully loaded, the d letters are then inserted into the top left part of the screen. As soon as the command prompt comes up, the d key stops working. The command prompt text flashes each time I press d, but nothing happens.

Neither can I copypaste text containing the d letter - every time I try, it just disappears from the pasted text. The key works everywhere else.

Help?

---

### Post by x1a4 on 2008-06-28
Hi, 

There might be an issue with your keyboard or text encoding--what are you using?  Also, r-click the terminal, click 'Properties' and check the 'Shortcuts' page, perhaps you have 'd' mapped to something.  Further, check the 'Advanced' page and look at the 'Backspace key generates' and 'Delete key generates' values.  Perhaps 'd' is generating a backspace or delete.  You should also check your shell's (what shell are you using?) and Xfce's key mappings.

Good luck.

EDIT: You shouldn't press anything until the shell is done loading and you see the prompt.

---

### Post by Aukikco on 2008-06-28
> **x1a4 said:**
> There might be an issue with your keyboard or text encoding--what are you using?
How do you check that?

> perhaps you have 'd' mapped to something.
nope.

> look at the 'Backspace key generates' and 'Delete key generates' values.
Set to "automatic".

> Perhaps 'd' is generating a backspace or delete.
nope.

> You should also check your shell's (what shell are you using?) and Xfce's key mappings.
Again, how to? :)

> EDIT: You shouldn't press anything until the shell is done loading and you see the prompt.
Normally wouldn't. Just noticed.

The d key seems to be working when pressing shift or when caps lock is on.

---

### Post by Aukikco on 2008-06-29
still not working...

---

### Post by lukjad on 2008-06-29
> **Aukikco said:**
> I have no idea of the cause, but I installed Xubuntu onto a friend's computer, and everything seemed to be working at first. However, during the second day of using, the d key stopped working in Terminal. When I start Terminal up, if I hit the d button before it has fully loaded, the d letters are then inserted into the top left part of the screen. As soon as the command prompt comes up, the d key stops working. The command prompt text flashes each time I press d, but nothing happens.

Neither can I copypaste text containing the d letter - every time I try, it just disappears from the pasted text. The key works everywhere else.

Help?

This will sound simple and stupid but...
Have you tried swapping keyboards? Maybe the "D" key is jammed or broken.
Also try changing the keyboard layout. It may just be a glitch.

---

### Post by x1a4 on 2008-06-29
> **x1a4 said:**
> There might be an issue with your keyboard or text encoding--what are you using?
[QUOTE=Aukikco;5280423]How do you check that?
[/QUOTE]
Check your keyboard settings in /etc/X11/xorg.conf or attach a different keyboard to see if it produces the same behaviour.  Also, r-click the terminal, open the 'Input Methods' menu and try the different ones.

> **x1a4 said:**
> look at the 'Backspace key generates' and 'Delete key generates' values. Perhaps 'd' is generating a backspace or delete.
[QUOTE=Aukikco;5280423]Set to "automatic".

nope.[/QUOTE]
How do you know?  Have you tried the others?


> **x1a4 said:**
> You should also check your shell's (what shell are you using?) and Xfce's key mappings.
[QUOTE=Aukikco;5280423]Again, how to? :)[/QUOTE]
If you don't know then that's not the problem.

Start by setting different backspace and delete characters and see which works.  It looks like your keyboard is generating something other than 'd' in the terminal.  Also, open another terminal (xterm for example) and see if this is happening there as well.  Further, hit Ctrl+Alt+F1, login as yourself and see if you have this in the console as well.

---

### Post by scliburn on 2008-11-14
I started to have this same problem over the last couple days. Mine dealt with the letter 'N'.

I discovered that my 'N' letter was remapped for the paste command. How? I have non clue. Maybe a fat finger syndrome, working to fast, and not waiting for the system to finish my requests. ;)

So anyway, discovered the issue, fixed the mapping and all is good now.

---

