---
title: "Run (perl) script in its own terminal"
date: 2007-07-08
forum: General Help
---

### Post by foamcarver on 2007-07-08
I am trying to start a perl script and have that script run in its own terminal (not the one I started it from)

Dose anyone know how to do this?  

For the bigger picture.  I have a perl script that I want to run at start up (log in)

I have run other programs at start up by adding them to list in system->preferences->session.  I can add the perl script here and it may be runnig,  but without a terminal to see the output it is not very useful.

I would like to add a command to the ->session list that starts a terminal (x-term or whatever) and runs my perl script in that terminal.

Thanks
Troy

---

### Post by foamcarver on 2007-07-08
Ok I figured it out.  I post my solution in case some one else has the same question

xterm -e will start a program in a new xterm.  In my case I use

xterm -e perl my_script.pl

Added that line to the sessions list,  easy enough but took me a while to figure out.

---

### Post by autobot on 2007-12-28
when I follow these instructions my perl script pops up in a terminal window and then disappears very quickly.  Thus, it is not running when I test it.  Any ideas?

---

### Post by dagnabit dang doohickey on 2007-12-28
Add the "-hold" option to the command:
```
xterm -hold -e perl my_script.pl
```

---

### Post by autobot on 2007-12-28
Thanks, but that didn't work.   It just left the terminal window up, but the perl script was not running.  It was really strange, I am not sure how to explain it, but the window was blank except for the first character on the left side of the screen for each sentence of the perl script that was running.

I can run the script fine in a terminal window with 


```
sudo xterm -e perl my_script.pl
```

Yet, when it is included in sessions the terminal pops up for a second and disappears, shutting down the script.

---

