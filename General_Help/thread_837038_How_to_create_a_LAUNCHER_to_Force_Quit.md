---
title: "How to create a LAUNCHER to Force Quit?"
date: 2008-06-22
forum: General Help
---

### Post by brett123 on 2008-06-22
How can I create a **LAUNCHER** (put it on the desktop, or dock etc) to activate the same function as Force Quit does (the one you add to panels)?

---

### Post by bikeboy on 2008-06-22
Nevermind. People make mistakes.

---

### Post by brett123 on 2008-06-22
No, no, I have that. That isn't the problem. I want to _add it to my desktop, not on a panel_.

---

### Post by benthegreat on 2008-06-22
> Right-click the panel and select "Add to Panel". Then find the "Force Quit" applet. That might do what you want. 
<snip>

He knows about the panel one, but wants one on a dock or his desktop. Unfortunately I'm none the wiser, could I ask why you want another?

---

### Post by ad_267 on 2008-06-22
You can create a launcher that will run xkill.

---

### Post by Oldsoldier2003 on 2008-06-22
> **ad_267 said:**
> You can create a launcher that will run xkill.
+1
As a reminder, if you make a launcher to run xkill you need to right click and select open to get the selection cursor. You can't double click the launcher and make it work.

---

### Post by ad_267 on 2008-06-22
> **Oldsoldier2003 said:**
> +1
As a reminder, if you make a launcher to run xkill you need to right click and select open to get the selection cursor. You can't double click the launcher and make it work.

I didn't realise that, I didn't actually try it until now. Why is that?

---

### Post by brett123 on 2008-06-22
benthegreat, the reason I wanna do this is so I can get rid of the top bar altogether - it's the only thing left that can't be docked or widgeted etc. 

And I do need it many times each day, therefore opening a terminal and typing a command would be a pain each time. I have an old "almost MS-DOS program" that I require for my work (there just isn't any updates and no further development will be done on it), and it doesn't close down (shut, exit, X, close, nothing works). It was like this under MS Windows as well (had to CTRL-ALT-DEL to kill it each time). The only way to close it is Force Quit.

xkill is a problem though. As someone said, you have to right click it, which means I can't add it to the dock (can't right click dock items). Adding it to my desktop is fruitless as the stupid DOS program is maximised (and you can't resize it) so I can't actually get to the desktop to right click the xkill.

Arrrrggghhh - should be so simple. Ha ha ha haaaa...

Plus, the icon I get when xkill'ing is not the same as Force Quit, which leads me to believe that _Force Quit is not just an xkill command_. There has to be something more behind it.

---

### Post by Oldsoldier2003 on 2008-06-22
> **brett123 said:**
> benthegreat, the reason I wanna do this is so I can get rid of the top bar altogether - it's the only thing left that can't be docked or widgeted etc. 

And I do need it many times each day, therefore opening a terminal and typing a command would be a pain each time. I have an old "almost MS-DOS program" that I require for my work (there just isn't any updates and no further development will be done on it), and it doesn't close down (shut, exit, X, close, nothing works). It was like this under MS Windows as well (had to CTRL-ALT-DEL to kill it each time). The only way to close it is Force Quit.

xkill is a problem though. As someone said, you have to right click it, which means I can't add it to the dock (can't right click dock items). Adding it to my desktop is fruitless as the stupid DOS program is maximised (and you can't resize it) so I can't actually get to the desktop to right click the xkill.

Arrrrggghhh - should be so simple. Ha ha ha haaaa...

Plus, the icon I get when xkill'ing is not the same as Force Quit, which leads me to believe that _Force Quit is not just an xkill command_. There has to be something more behind it.
I realize that this is not really what you want to hear, but in your case i would probably just launch a terminal using ALT+F2 and if that didnt work (some configurations of compiz tend to break that) I would CTRL+ALT+F1 to a console and kill the offending app from there. CTRL+ALT+F7 returns you to the xserver.

---

### Post by brett123 on 2008-06-22
Thanks. I was looking at *alternate* 'solutions' now too.

I just realised/learnt two things:

1) System Monitor has a kill process option that MS Windows people are used to seeing, and it can be added to the dock obviously.

2) ALT-F4 actually does kill this dodgy DOS program of mine (it never did under Windows).

So, yeah, I'm happy.


Got some hints from here:
[http://cubicledenizen.blogspot.com/2008/02/kill-frozen-x-application-under-ubuntu.html](http://cubicledenizen.blogspot.com/2008/02/kill-frozen-x-application-under-ubuntu.html)

---

