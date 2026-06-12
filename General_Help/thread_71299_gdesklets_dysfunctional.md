---
title: "gdesklets dysfunctional"
date: 2005-10-02
forum: General Help
---

### Post by xturmn8r on 2005-10-02
I installed gdesklets & gdesklets-data from synaptic, and when I tried to run them, only some worked, and most just had a black background... also, the tip of the day comes up blank... is this a common n00b issue? if so (or even if not ;)   ) I need help with this.. 
TY!
\/ a picture of what I'm talking about
[[IMG]http://img134.imageshack.us/img134/4471/help0lx.th.jpg[/IMG]](http://img134.imageshack.us/my.php?image=help0lx.jpg)
also, the CPU monitor says I need lmsensors installed and working... well, it's installed, how do I get into it and make it work?   thx again

---

### Post by munitras on 2005-10-03
i have read on these forums that the gdesklets-data package breaks the whole thing. 
try removing it. maybe with (although i'm not 100% sure this will work as i have not done it myself.
```
sudo apt-get remove --purge gdesklets-data
```
i'm running gdesklets (without the data package) and all is fine.

---

### Post by xturmn8r on 2005-10-03
sweet! That worked!   now I just have the transparency issue, any ideas on that one?   Thanks!

---

### Post by jasay on 2005-10-03
If I remember correctly, go to the gdesklets configuration (right click on the notification area icon on the bottom right of your screen) and unclick translucency (rather counter-intuitive, no?).  Then restart gdesklets.  Anyway, won't hurt to try as you can just undo it.

---

### Post by One2 on 2005-10-03
> i'm running gdesklets (without the data package) and all is fine.Same here... The Desklat-data contains obsolete stuff.

---

### Post by xturmn8r on 2005-10-03
bingo! alright... next to tackle: Sudoku ;-) I'll let you know of my progress ;-)   Many thanks!

---

