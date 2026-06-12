---
title: "3: command not found - Top of Terminal"
date: 2014-11-16
forum: General Help
---

### Post by musicboy on 2014-11-16
I've searched the internet, I've searched the forum, no information on this, other people getting errors but not how to fix this and I am STUMPED!

Late last night I opened my terminal in Ubuntu and at the top of the terminal before my username/computer name etc it says 'above it' directly '3: command not found' and I have no idea why or how to fix this?

Can someone please help? I would be extremely grateful.

Thanks,

Studiofreak :guitar:

---

### Post by matt_symes on 2014-11-16
Hi

No idea what is causing this but do you still get the error if you call top directly ?

```
/usr/bin/top
```

Kind regards

---

### Post by musicboy on 2014-11-16
its always there at the top but this command just opens up the command its self and then

top - 17:43:08 up 59 min,  2 users,  load average:Tasks: 259 total,   4 running, 255 sleeping,   0 s
%Cpu(s): 17.8 us, 15.7 sy,  0.0 ni, 65.8 id,  0.2 
KiB Mem:   8176252 total,  4496632 used,  3679620 
KiB Swap:  8387580 total,        0 used,  8387580

---

### Post by steeldriver on 2014-11-16
There seems to be some confusion here between the **location "**top" (within the terminal window) and the top **command** - if you are seeing a line like

```

3: command not found

```

every time you open a new terminal window, that's most likely comming from some rogue command in your ~/.profile or ~/.bashrc file

---

### Post by matt_symes on 2014-11-16
Hi

> **steeldriver said:**
> There seems to be some confusion here between the **location "**top" (within the terminal window) and the top **command** - if you are seeing a line like

```

3: command not found

```

every time you open a new terminal window, that's most likely comming from some rogue command in your ~/.profile or ~/.bashrc file

Agreed. 

I msunderstood your question and thought the top command itself was causing you the problem.

However, if you are only seeing this when you open a terminal, it will be some text in one of your shell initialisation files.

You may want to post them here

Kind regards

---

### Post by musicboy on 2014-11-16
Thanks for the pointers I solved it it was the /.bashrc file. It was a mistake from messing around with dssi-vst and prestige and trying to get them to work, which I haven't yet but I will keep trying. I know why this happened now thanks

Regards,

Studiofreak :guitar:

---

