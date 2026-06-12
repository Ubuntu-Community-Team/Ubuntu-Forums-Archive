---
title: "Remove Session Startup Program From Command Line"
date: 2007-01-26
forum: General Help
---

### Post by zitanos on 2007-01-26
ok so i just did a fresh install of edgy, then i followed the ubuntu guide and installed the nvidia drivers along with beryl/aiglx..

when i tried to start beryl-manager from the terminal i got:
XGL Absent, checking for NVidia
NVidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVidia
NVidia Present

and my comp hangs.. well my mouse could still move around, but i cannot click/open/close or do anything..

by mistake i added beryl-manager to the     
    * System -> Preferences -> Sessions
    * Startup Programs -> Add 

so now after the initial splash screen the computer hangs.. i'm guessing cause it's trying to start the beryl-manager

seeing as i can't remove it... because it's only hanging after boot...
how could i remove it from the command line??


thanks.

---

### Post by eggdeng on 2007-01-26
The command(s) you added in the startup programs dialog box will each have created a file in the directory  /home/username/.config/autostart.
Type ```
ls /home/username/.config/autostart
```
to se what files you have
then```
sudo rm  /home/username/.config/autostart/filename
```
to delete unwanted files.

---

### Post by zitanos on 2007-01-30
ok this worked... thank you very much

---

