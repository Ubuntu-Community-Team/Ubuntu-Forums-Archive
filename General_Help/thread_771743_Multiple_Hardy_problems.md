---
title: "Multiple Hardy problems"
date: 2008-04-27
forum: General Help
---

### Post by kgriff on 2008-04-27
I have two computers loaded with Hardy.  One is having problems, while the other is not.  Hopefully, someone can help me solve these issues.  If not, it&#347; not a big deal to reload Hardy, but I´d like to know what´s causing these issues.

This has happened from the beginning, as soon as installation was complete.
When running any program that requires sudo login, I have to run the program multiple times before I am prompted to login.  For instance, if I run, from terminal, sudo apt....., nothing happens.  If I close terminal, and re-run the command, after 7-10 seconds I get the login prompt.  In contrast to my other machine, where the login prompt shows up almost immediately.

The following happened progressively, in the order below:
1.  Programs take a long time to run.  Virtually every program on this machine takes twice as long or longer to run than on the other machine.  The slow machine is running an Athlon dual core 5200+ at 2.7GHz with 2GHz ram.  The non-slow machine is running an Athlon single core at 2.4 GHZ with 512 MB ram.  Watching top or System Monitor does not show any significant drain on resources.
2.  Programs are not displayed on the lower taskbar as they are opening.  In and of itself, this is not a big deal, but I think it relates to problem 3.
3.  When I minimize a program, it disappears.  The program doesn´t close, because I can still see it in top or System Monitor, but I cannot restore it.  Programs do not minimize to the taskbar.  Apparently, they minimize to Never Never Land.

Help??


edit:  Nevermind on 2 and 3.  I figured those out.  Turns out, the Window List panel applet had gotten squished to the far left, left of the default location for the show desktop applet.  It was there, I just couldn´t see it.  Not sure how this happened, but I´m positive I didn´t mess with any of the panel applets.

---

### Post by bingoUV on 2008-04-27
**Prompt does not appear promptly**
    Have you tried creating a new user and logging in graphically through that user?

**Slow**
1. Athlon CPU means[INDENT]         No intel graphics drivers. Which means 
[/INDENT][INDENT][INDENT]                Possibly closed source graphics driver.  Means[INDENT]Trouble[/INDENT][/INDENT][/INDENT]2. Single core athlon suggests possibly older graphics card. It means[INDENT]          Maybe issues with its linux driver are better sorted out than newer graphics card.
[/INDENT]Of course all this is pure speculation. Post the graphics card on both the systems. If they are discrete graphics cards,
 try swapping them. Have you enabled desktop effects?

---

### Post by kgriff on 2008-04-27
I haven´t created a different user.  Never even thought about that, but will do it and post results.

Older, single core machine has graphics on mobo.  Nvidia 6-class chipset.

Dual core machine has discrete grahpics card.  Asus Nvidia 8400.  I´ve seen many posts by people with problems with the Nvidia 8xxx series, but I wouldn´t have linked that to an overall system slowdown.

---

### Post by ryanhaigh on 2008-04-27
Is there some rogue process using all your cpu, you can check with the system monitor in system>admin, or using top from the commandline.

---

### Post by kgriff on 2008-04-27
No desktop effects enabled on the slow account.

Created a new user and logged in as that user.  Like magic, everything is super-fast.  So, what gives?  I realize I could simply delete the old account and all should be well, but what would cause a slow down on one user account?

Response to ryanhaigh:  There is nothing sucking up cpu or ram.  That was the first thing I checked.

---

