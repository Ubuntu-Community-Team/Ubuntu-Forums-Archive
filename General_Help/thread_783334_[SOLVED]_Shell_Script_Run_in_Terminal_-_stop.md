---
title: "[SOLVED] Shell Script Run in Terminal - stop"
date: 2008-05-05
forum: General Help
---

### Post by jpietari on 2008-05-05
I have sqldeveloper on my PC, which requires you to open it using a shell script (sqldeveloper.sh).  Every time I do this, I get prompted with "Do you want to run 'sqldeveloper.sh', or display its contents?".  

How do I configure this to automatically run the shell script?

---

### Post by mike2357 on 2008-05-05
You could try creating a "Custom Application Launcher", assuming you are using the Gnome desktop.

Right-click in an empty area of one of your panels, select "Add to Panel", then "Custom Application Launcher", then "Add".  In the "Command" space, type a full path to sqldeveloper.sh, such as:
/usr/local/bin/sqldeveloper.sh

After you create the launcher, simply clicking on it should start sqldeveloper.sh.

---

### Post by jpietari on 2008-05-06
That is exactly what I was looking for. 

Thanks for your help!

---

