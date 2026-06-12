---
title: "disable compiz from terminal"
date: 2008-05-08
forum: General Help
---

### Post by ant2ne on 2008-05-08
I want to write a script that will disable compiz and revert to the boring windows manager while I run some games. Then Another command to re-enable compiz when I'm done.

---

### Post by Therion on 2008-05-08
[Compiz Switch](http://forlong.blogage.de/article/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on)?

---

### Post by mano cazalet on 2008-05-08
it is already in repos and called fusion-icon

---

### Post by ant2ne on 2008-05-14
> **ant2ne said:**
> I want to write a script that will disable compiz and revert to the boring windows manager while I run some games. Then Another command to re-enable compiz when I'm done.
Command line

---

### Post by Genius314 on 2008-05-14
You could try replacing the shortcut command for the game with something like:
```
metacity --replace && (game command) && compiz --replace
```
But I'm not a Linux or Ubuntu guru, so I don't know exactly how well that would work.
(Also... it might be "emerald --replace"... not sure, it's been a while since I've run compiz-fusion from a command line)

You probably should try Fusion-Icon, as suggested, and just switch with that.

---

### Post by ant2ne on 2008-05-15
> **Genius314 said:**
> You probably should try Fusion-Icon, as suggested, and just switch with that.Fusion-icon is a wonderful tool for crashing my X. No thanks.

---

