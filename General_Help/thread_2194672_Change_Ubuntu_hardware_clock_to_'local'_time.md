---
title: "Change Ubuntu hardware clock to 'local' time"
date: 2013-12-19
forum: General Help
---

### Post by s.boone35223 on 2013-12-19
I have read multiple articles about changing Ubuntu hardware clock to 'local' time to fix an incompatability with clock settings in dual boot (Windows/Ubuntu) systems.  I am guessing the "edit" command is entered in Terminal and that you must be at the Root partition?  If correct, can someone tell me how to navigate to the Root partition?  Thanks.  
[B]
Make Linux use 'Local' time[/B]

 To tell your Ubuntu system that the hardware clock is set to 'local' time:

[LIST=1]
[*]edit /etc/default/rcS 
[*]add or change the following section # Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no 
[/LIST]

---

### Post by Irihapeti on 2013-12-19
You need to have root privileges, which means using sudo.

For example:

```
sudo nano /etc/default/rcS
```

and enter your login password. You won't see any *** symbols when you type it, but it's still working.

If you want to do it in two steps, you can
```
cd /etc/default     ##takes you to the directory
sudo nano rcS
```

nano is a code editor that works in the terminal. There are other terminal editors, but nano is probably easier for a beginner than some of the others.

---

### Post by mc4man on 2013-12-19
In case it isn't apparent, after making edit in nano - 
ctrl+o
enter key
ctrl+x

---

### Post by s.boone35223 on 2013-12-20
Thank you.  Both responses did the trick.

---

