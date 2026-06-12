---
title: "Emerald Theme Problem"
date: 2008-05-30
forum: General Help
---

### Post by wikwanderlust on 2008-05-30
Hate to bother everyone with my extreme n00bness...But I have no choice, so here goes.

I'm using Emerald Theme Manager, and for the most part, it's working fantastically. What's happening though, is I have to type "emerald --replace" in a terminal to get the themes to show up. That's all well and good, but when I close the terminal, I lose my window borders until I open another terminal and retype "emerald --replace". It would nice If I didn't have to type the command and leave my terminal open, and it would be nicer still If I could get the Emerald themes when my computer started automatically without having to do anything.

This is probably a laughably simple problem, I just don't know my way around Ubuntu (or Linux in general) well enough yet to fix these things.

---

### Post by fickenbaisage on 2008-05-30
> **wikwanderlust said:**
> Hate to bother everyone with my extreme n00bness...But I have no choice, so here goes.

I'm using Emerald Theme Manager, and for the most part, it's working fantastically. What's happening though, is I have to type "emerald --replace" in a terminal to get the themes to show up. That's all well and good, but when I close the terminal, I lose my window borders until I open another terminal and retype "emerald --replace". It would nice If I didn't have to type the command and leave my terminal open, and it would be nicer still If I could get the Emerald themes when my computer started automatically without having to do anything.

This is probably a laughably simple problem, I just don't know my way around Ubuntu (or Linux in general) well enough yet to fix these things.

This is a problem when using the terminal to run programs, your programs close when you close the terminal. Learn to use ALT+F2 to run applications, for your case press "Alt+F2" and type in "emerald --replace" without the quotes.

---

### Post by cubeist on 2008-05-30
> **wikwanderlust said:**
> Hate to bother everyone with my extreme n00bness...But I have no choice, so here goes.

I'm using Emerald Theme Manager, and for the most part, it's working fantastically. What's happening though, is I have to type "emerald --replace" in a terminal to get the themes to show up. That's all well and good, but when I close the terminal, I lose my window borders until I open another terminal and retype "emerald --replace". It would nice If I didn't have to type the command and leave my terminal open, and it would be nicer still If I could get the Emerald themes when my computer started automatically without having to do anything.

This is probably a laughably simple problem, I just don't know my way around Ubuntu (or Linux in general) well enough yet to fix these things.

Alt-F2 and type
```
emerald --replace
```
 
You could also add this command to your sessions list to get emerald running after boot-up

---

### Post by robertchahine on 2008-05-30
i had a problem like this.
but i just typed emrald --replace and reboot the pc.
and everything work well

---

### Post by wikwanderlust on 2008-05-30
And once again, the day is saved! Thanks guys, problem (or lack thereof) solved.

---

### Post by cubeist on 2008-05-30
> **robertchahine said:**
> i had a problem like this.
but i just typed emrald --replace and reboot the pc.
and everything work well

No, just typing it once (either in a terminal or with alt-f2) will not save it.  To have emerald come up after boot, it has to be in sessions (or somewhere else where your init will catch the command)

---

