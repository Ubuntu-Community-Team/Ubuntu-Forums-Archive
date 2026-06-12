---
title: "How do I get out of this screen?"
date: 2017-06-16
forum: General Help
---

### Post by juntjoo2 on 2017-06-16
I was trying to close some app by instructions from a page on how to simulate ctrl+alt+del in Windows and tried a solution and got stuck here. I logged in but didn't know what to do from there.Btw, since I'm here, can anyone tell me how to get a task manager up like u do I  windows. I'd prefer a method just as easy. I actually tried to create a keyboard shortcut as someone suggested but the instructions were incomplete. To create a keyboard shortcut I got stuck after making a name for it. After that there was just this empty box prompting me like an open ended question for info I've none of. 

Thanks

[ATTACH=CONFIG]275678[/ATTACH]

---

### Post by Bashing-om on 2017-06-16
juntjoo2; Hey --- hey .

That is a "terminal" prompt where you are .

It is asking for your username .
Once your username is entered will ask for your pass word. Enter the password you created when you installed the system.
there will be no response to the screen when the password is entered - security .

Once you are logged into the system from this terminal then one can return to the GUI desktop with key combo ctl+alt+F7 on most keyboards/DEs .

What Desktop Environment are you running ? as the task manager is generally installed by default in the GUI . ( its a GUI application !)

In terminal there are many tools to look at the system . Just depends on what the end goal is as to the tool one uses .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by juntjoo2 on 2017-06-16
Thanks. You got me back. But I'll forget that lol. Is there another command from there to exit like "exit"?? 

As far as my end goal, I just want to kill a stuck task which happens from time to time. What's the best path for this? Thanks!

I'm pretty sure I'm running KDE

---

### Post by Bashing-om on 2017-06-16
juntjoo2; Well .

Yeah, to exit a terminal the command ' exit '  will get ya out of it ( ya want a means though to continue access to the system ! ).

As to killing a process .. that is ' kill <PID> ' ; Get that PID from an incantation of the 'ps' command.
There are GUI means also to do this . but I have no experience with it - will not say what I do not know .
see:
```

man kill
man ps

```

[INDENT][INDENT]welcome to system administration
[/INDENT][/INDENT]

---

### Post by oldos2er on 2017-06-16
Ctrl-Esc used to bring up a process list in KDE 4.x, I don't know if it still works that way in 5.x. Or you can hit Alt-F2 to bring up krunner and enter *xkill*, then click in the window you want to die. xkill is in the package x11-utils which I don't think is installed by default.

---

### Post by ajgreeny on 2017-06-17
I seldom need to use it but many years ago I created a keyboard shortcut for xkill of Win-key+Del. It works very well when needed, but that is not very often.

---

### Post by vasa1 on 2017-06-17
> **juntjoo2 said:**
> ...
I'm pretty sure I'm running KDE
You could post the output of```
echo -e "Version $(lsb_release -drc)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Kernel info: $(uname -r)"
```to give something like```
07:06 AM ~ $ echo -e "Version $(lsb_release -drc)
> Session: $DESKTOP_SESSION
> Desktop: $XDG_CURRENT_DESKTOP
> Kernel info: $(uname -r)"
Version Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
Session: plasma
Desktop: KDE
Kernel info: 4.4.0-79-generic
07:06 AM ~ $ 
```

---

