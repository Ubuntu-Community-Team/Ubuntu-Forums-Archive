---
title: "exit process in terminal"
date: 2007-04-04
forum: General Help
---

### Post by pgn674 on 2007-04-04
I'm wondering if it's possible to end a process in the command line (Terminal), with the same effect as using System Monitor to kill or end the process.

In System Monitor, when you right click on a process, you can, amongst other things, "_K_ill Process" and "End _P_rocess". In terminal, you can type ```
kill $(pgrep beryl)
``` to kill the process beryl. It seems to be stronger than System Monitor: the process is forced to exit immediately, no questions asked, no work saved, no cleanup done. The man page for kill gives a bunch of signals you can send, but those that seem to be like kill (quit and term) have the same effect.

What I'm trying to do is this: I have Beryl, and always have it running, with Beryl set as my window manager. But, I also want to VNC into my computer from afar time to time. This works nicely when I have Metacity set as my window manager, but with Beryl selected, it all I get is a screen shot when I connect. I can still send mouse movements and clicks and keyboard presses, I just don't get a refreshed screen. This is a known issue, and has to do with the way Beryl handles 3D screen refreshes.

Anyways, I want to make a shortcut on my Panel that links to a shell script that I'll write. The shortcut will be easy to press with a single image of my screen. Using System Monitor, I can end or kill the process beryl, which asks Beryl to nicely quit itself, and lets Beryl activate its "Launch Fall-back Window Manager if beryl crashes" option, and switches the window manager to Metacity.

But, using kill in terminal forces beryl to quit immediately, and I end up with no window manager running (not a pretty, or usable, sight). It seems to take down the process beryl-manager too, which System Monitor doesn't do.

So, is there a way to use terminal to quit a process in a similar manager as System Monitor?

---

### Post by irwa82 on 2007-04-05
Hi,

try this and see if it works

$ kill -15 $(pgrep beryl)

---

### Post by fdrake on 2007-04-05
if that doesn' work try this:
ps -e (find beryl's PID number and copy it)
kill -9 <PID> (without <>)

---

### Post by pgn674 on 2007-04-05
Ohh, I see what's going on. Thanks, fdrake, your suggestion worked.

There are two processes running with Beryl. One is called "beryl", the other is "beryl-manager". Killing beryl-manager then beryl has the undesirable effect that I was experiencing. Running
$ pgrep beryl
   returns 2 numbers: beryl's and beryl-manager's PID's. So, I was killing both processes, when I just wanted to kill beryl.

So, now I just need to figure out how to automatically kill just beryl, without manually looking up its PID in person.

---

### Post by pgn674 on 2007-04-05
OK, ```
$ kill -15 $(pgrep beryl$)
``` did it. Putting $ in the text to match means that's the end of a line. So it doesn't return beryl-manager.

---

