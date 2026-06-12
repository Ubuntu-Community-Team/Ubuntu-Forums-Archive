---
title: "conky script running at login"
date: 2017-03-25
forum: General Help
---

### Post by alain.roger on 2017-03-25
Hi,

i'm using KDE under ubuntu and before i had a script in home/alain/bin/conky_start that run 3 different conky scripts.
However only 2 scripts are running and i was wondering why.

i went to KDE option from configuration to "startup & shutdown" and i disable and remove the 1 running script that should execute all 3 conky script.
However, after rebooting my laptop, once again conky scripts are executed.
I check if i had something in .bashrc but no line about conky...

So what's going on ?
From where those 2 conky scripts are executed ?

thx for you help, because i'm loosing my mind trying to figure it out.

---

### Post by vasa1 on 2017-03-25
See if```
ps -o pid,ppid,stime,time,command -H -u $USER
```or```
ps -HF -u $USER
``` gives you a hint.

---

### Post by alain.roger on 2017-03-25
this is the output:
```
[FONT=monospace][COLOR=#000000] 3094     1 21:35 00:00:05 conky -c /home/alain/.conky/.conkyrc_top_middle[/COLOR]
 3092     1 21:35 00:00:12 conky -c /home/alain/.conky/.conkyrc_top_right
[/FONT]
```

so the parent process id is 1 :( no more idea what execute those 2 scripts :(

i thought i would find what process run them but it seems that root process run them.... based on what ??? i'm lost :(

---

