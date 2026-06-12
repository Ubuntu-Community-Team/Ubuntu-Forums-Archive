---
title: "Little difficulty here"
date: 2007-02-05
forum: General Help
---

### Post by telmo on 2007-02-05
Hi, i'm using fluxbox and i'm trying to create a command line to open the terminal (xterm) in a specific place or to open a specific command as root. I've tried gksudo xterm <command> but the terminal window always closes. I really need this badly...

Is there a way to do this right?

Thank you.

---

### Post by schilcha on 2007-02-05
If you just need to see the output of that script, try:
```

gksudo xterm -hold <command>

```
This will keep the xterm-window open until you actively close it.

If you also need a root-console afterwards, try
```

gksudo xterm -e '<command>; bash'

```
This will execute <command> and start bash afterwards, which will keep the xterm open until you exit bash (or close the window).

Good Luck!

---

### Post by telmo on 2007-02-05
Thank you so much! That was exactly it! I got a pm with it just before you wrote it. That works beautifully!
I was reading all the xterm manual and trying different commands, but i didn't remembered to try that one... :)
The -hold command wasn't enough for me. I wanted the console to be normaly opened.

Thank's again! ;)

---

