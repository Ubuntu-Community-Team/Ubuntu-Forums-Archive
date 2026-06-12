---
title: "Where is my gkrellm?"
date: 2008-06-22
forum: General Help
---

### Post by carl99fan on 2008-06-22
Last night I was looking for a program like Everest to obtain info about my motherboard.

I installed gkrellm through my package manager, I also installed plenty of plugins that sounded fun...

Problem for me right now is I can't find it! lol
I can run it through my terminal but I'm not sure where it is...Seems I have looked all over.
If anybody can tell me where I might find it in home, or apps, or system,I would love it.

I thank you in advance.
I am using hardy 8.04

---

### Post by atomkarinca on 2008-06-22
The executable should be  /usr/bin/gkrellm and the configuration files should be in ~/.gkrellm2.

---

### Post by spiderbatdad on 2008-06-22
you can create a launcher for it quite easily, either through the main menu in System>Preferences>Main Menu or by right clicking on the panel and selecting 'add to panel.' 'Custom Application Launcher.'

---

### Post by windoze87 on 2008-06-22
if for some reason gkrellm isnt in /usr/bin/, you can do this in terminal:```
which gkrellm
``` as the poster above me said, you can create a custom launcher, or you can set gkrellm to run at startup too. if you want it to run at startup, go to System>Preferences>Sessions, click Add, fill in whatever you'd like for name, and under command type /usr/bin/gkrellm (if it isn't in /usr/bin/, type in the path where it is located)

---

### Post by carl99fan on 2008-06-22
AWESOME!!

Thanks guys, I would have never found it! LOVE these forums!!:guitar:

---

### Post by carl99fan on 2008-06-22
To make a quick launch, I just dragged it to the bar and created it that way... never even knew I could do that!!

Hardy is awesome.

---

