---
title: "How to kill processes?"
date: 2006-07-09
forum: General Help
---

### Post by hansoffate on 2006-07-09
Some times my linux crashes.  Then I get to a terminal, ctrl+f1 or something (if you could tell me aht would be good).  Anyways, I know there is a way to kill processes or restart just your desktop environment.  


Is there a guide on this?  Or could somone tell me how?  Basically, I want to know how to enter a terminal, kill whatever process i want to kill, then restart into my desktop envrionment. 

I tried looking on the forum but I coudln't find anything.


Thanks for the help
-Hans

---

### Post by tonyr on 2006-07-09
You can use the command **ps aux** to see all the running processes.
You can use the command **ps aux | grep <something>** to see only
the processes that have the **<something>** you are interested in.

Then when you have a **<unique-something>** identified, you can use the
command **sudo pkill <unique-something>** to kill the process.

You can also use the command **kill** with one or more
**process id-numbers** (part of the output of **ps aux**).

You can also use the program **top** to see a list of running 
processes, and kill the ones you own.  You might be able to run
**sudo top** and kill anything.

The commands to stop and restart gdm (or kdm) are
[B]sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start[/B]
from the CTL+ALT+F1 console.

---

### Post by Jucato on 2006-07-09
If you want to just restart your desktop quickly, you can press Ctrl+Alt+Backspace. This restart's the X graphical engine. Take note that this is "almost" like pressing the restart button on your PC, meaning that if you were working on something, changes won't properly be saved. The only difference is that it doesn't have any bad effect on your filesystem.

---

### Post by hansoffate on 2006-07-09
Thank you.  Both posts where exactly what i was looking for.

-Hans

---

