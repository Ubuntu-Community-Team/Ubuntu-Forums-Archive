---
title: "[SOLVED] Console font issues"
date: 2008-06-07
forum: General Help
---

### Post by kriukov on 2008-06-07
I recently switched from Ubuntu 6.06 to 8.04. I don't seem to figure out how to turn off the unusual font on the console when the system boots up. In Dapper, there was just the regular one, but when Hardy boots up, it gives the message "Starting up" in a regular font and then it changes. 

After some googling, I managed to turn it off at the final stage using "VGA" instead of "Fixed" in the console font setup, i.e., it changes during boot-up but then comes back to normal.

How do I turn off the new font altogether? I don't even understand why one had to implement this.

---

### Post by drs305 on 2008-06-07
I am not completely clear as to which stage of booting you are referring to. StartUp-Manager  (System, Admin, StartUp-Manager) has an Appearance tab to set the themes, fonts, etc during boot. In another tab is the option to view or not view text during boot. Don't know if this is the process you are referring to or not. 

If you don't see StartUp-Manager:
```
sudo aptitude install startupmanager
```

---

### Post by kriukov on 2008-06-07
I meant the console mode before gdm comes on. I do not use any splash screens during boot-up.

---

### Post by kriukov on 2008-06-28
Solved:

sudo apt-get remove console-terminus

---

