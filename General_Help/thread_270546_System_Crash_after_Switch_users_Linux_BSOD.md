---
title: "System Crash after Switch users: Linux BSOD"
date: 2006-10-03
forum: General Help
---

### Post by tebibyte on 2006-10-03
The system crashes after I login, switch users, login, and switch back
Step 1: Login User: max
Step 2: switch users and log in as student user
Step 3: switch users and log in as max
popup:
about being aready logged in, click "return to previous"

The system crashes

Output:
1 dispay flickering
2 gui popup: "the greeter application appears to be crashing. Attempting to us a diffrent one" hit enter
3 repeat steps 1&2 four times
4 Linux blue screen of Death "The display server has been shut down about six times in the last 90 seconds. It is likely that something bad is going on. Wait for 2 minutes before trying agian on display :0"

I am using Edubuntu on a Dell Dimension 2350. No idea about graphics cards.

INcluded are several log files

The crashes happened around 13:21-13:35

Should i file a bug report???

---

### Post by divineleft on 2006-10-03
I have the same problem, haven't been able to figure it out.

---

### Post by cptnapalm on 2006-10-03
Not quite a Blue Screen of Death... more of a Blue Screen of X.. Blue SoX :)  The underlying system is still running, unlike a BSOD.  Anyway.

I only do nested logins, so this is my best guess as to what is happening:

There are two instances of X starting on VT7 and VT8 (I think), respectively to take care of each user.  Fullblown GDM dies and then can't start up the somewhat stripped down version either.  So X gives up the ghost.

Are you left at a command prompt, login or otherwise?  If it stays on the blue screen, then try this:
Ctrl-Alt-F7
if nothing useful, then
Ctrl-Alt-F8
if nothing useful, then
Ctrl-Alt-F1

Assuming that X going down hasn't somehow taken out keyboard input, the last ought to get you to a command line.  If you have sudo priveleges, /etc/init.d/gdm stop and then /etc/init.d/gdm start

If it can, GDM and X with it, will completely die (hopefully) and then try to start anew.

I would recommend filing a bug report as this is no doubt not what it is supposed to be doing.

---

### Post by tebibyte on 2006-10-04
I can't switch to tty5 6 or 7 after the crash. THe Caps Lock light on my keyboard, cannot be toggled. IT looks like a complete system failure to me.

---

### Post by tebibyte on 2006-10-04
I submited a bug report [HERE.]("https://launchpad.net/distros/ubuntu/+bug/64023")

---

### Post by tebibyte on 2006-10-06
[This is my computer in the hardware database.]("http://hwdb.ubuntu.com/?xml=ad211190cd411be556b74e4be7f6956a")

---

### Post by tebibyte on 2006-11-01
I did a fresh install of edgy, on the machine that was running Dapper. Afterwards, the bug was unable to be reproduced. However the bug should still be checked out, because Dapper is a LTS realease. I wonder the bug has been eliminated in all installations of edgy?:confused:

---

