---
title: "software shutting down"
date: 2007-05-19
forum: General Help
---

### Post by Bashed on 2007-05-19
Software are shutting down abruptly for no reason at all, even after full reboot.

I'm using Ubuntu Feisty Fawn.

The software that are shutting down abruptly are:

Galeon browser
Azareus

These two are the only ones I encountered this issue with so far.

---

### Post by mbradlcu on 2007-05-20
if you haven't already, run the programs from the command line and see if they generate any errors... you may also want to try running the programs with --help appended to them and look for a verbose output to see more detailed output.
If you want to have more fun run:
```
sudo tail -f /var/log/messages
```
while running the programs.

---

