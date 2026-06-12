---
title: "Launch app in background"
date: 2008-05-12
forum: General Help
---

### Post by AcidHawk on 2008-05-12
I noticed something that i didn't understand and perhaps the folk here could assist me.

Open a shell and run the following
```

gedit &

```
If you type exit at the shell the gedit editor remains open on your screen but the shell closes.

Do it again...
In the same shell you can run cmds etc.... 
**However**, if you click on the "X" windows widget to close the shell the gedit editor also closes?

Huh?  Why is this?

---

### Post by hermes0710 on 2008-05-12
I suppose the "exit" command checks if there are processes started by the "process" of the console and since there are, it terminates the parent without affecting the child (leaving parent in sleep mode, still running) until child dies. If you press the X widget you force the process of the console to be killed, killing all children. 

These might not be accurate but you can try the following. Open the system monitor and then open a terminal and locate in the system monitor the entry for the terminal's process. Run gedit in the background and exit the terminal typing "exit". Is the entry from the system log removed?

Then do the same thing but this time close the terminal through the widget.

---

### Post by AcidHawk on 2008-05-12
Thanks for the quick reply hermes0710.

I did as you suggested.

1. Opened System Monitor
2. open a new console
3. echo $$ from console to get pid
4. found pid in system monitor
5. run gedit & from console and see gedit window open
6. type exit in console

the gedit windows stays open but the pid in system monitor for the console disapears.

ie. I think the console process is destroyed.

---

### Post by hermes0710 on 2008-05-12
It sure does as you say! Hmmm... It then must have to do with the difference between killing and terminating a process... I don't know... If I find out something I'll get back to you. 

Interesting notice though :confused:

---

### Post by AcidHawk on 2008-05-14
Bump.

---

### Post by bwphilip on 2008-05-14
If you'd like to prevent this from happening after logging out of the terminal, you can type in:
```
nohup gedit &
```

For more on the nohup command: [http://en.wikipedia.org/wiki/Nohup]("http://en.wikipedia.org/wiki/Nohup")

---

### Post by AcidHawk on 2008-05-14
Thank you bwphilip.  Any Ideas why this happens... I am busy looking up what nohup does...

---

### Post by bwphilip on 2008-05-15
No prob :) If you read the 'modern usage' section of [http://en.wikipedia.org/wiki/SIGHUP](http://en.wikipedia.org/wiki/SIGHUP) that is what I *believe* is happening when you close a terminal: Its signalling the programs you started to end as well. I may not be right 8-[

---

