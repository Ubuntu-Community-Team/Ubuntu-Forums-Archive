---
title: "Screen Going Black"
date: 2018-05-31
forum: General Help
---

### Post by trakyan on 2018-05-31
So I've just installed ubuntu 18.04. The live image was working fine and I started the install but had to leave so I left it to do its own thing.

When I came back, the computer has fallen asleep, but continued with the install when I woke it up. However, once I woke it up I noticed it would constantly switch the screen off and I think enter suspend.

I recall reading something about this possibly being caused by a false trigger of closing the laptop, but I can't find the thread (or solution) anymore. Could anyone give me a hand and point me in the right direction? At the moment I can't do much on the computer, at best I have less than a minute of functionality before it switches off.

---

### Post by cruzer001 on 2018-05-31
Going to console should stop the sleep cycle.
When you get to either the login screen or to your desktop press:
> Ctrl + Alt + F1
And your now on tty1.  You can now try some repair commands:
```
sudo dpkg --configure -a && sudo apt -f install
```
Post (best you can) any errors.
If successful switch back to your desktop:
> Ctrl + Alt + F7

---

### Post by trakyan on 2018-05-31
Ctrl + alt + f1 logs me out of the desktop rather than opening the console. Ctrl + alt + f7 sends me to a black screen which seems to be waiting for a text input, but I can't type anything. After a while it prints an i/o error
[(numbers)] system-gpt-auto-generator [(numbers)]: Failed to dissect: inputs/outputs error

I managed to run the bit of code through the terminal and no errors. Nothing got upgraded or installed, just 38 not upgraded.

EDIT: I should probably mention I decided to do a dual boot (in case something like this happens, so I'm not stuck without a computer since I can't afford to replace it). Not sure if that changes anything.

---

### Post by trakyan on 2018-06-01
I found a solution and I thought I'd post in case anyone else has the same issue.

I was right, it was a false "lid closed" triggering. I installed gnome tweaks, disabled power off when lid closed and the problem was solved.

---

