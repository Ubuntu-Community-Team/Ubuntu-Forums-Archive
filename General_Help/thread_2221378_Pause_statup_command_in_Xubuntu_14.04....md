---
title: "Pause statup command in Xubuntu 14.04...?"
date: 2014-05-01
forum: General Help
---

### Post by RallyDarkstrike on 2014-05-01
Hi all,

I've recently installed Conky on an older desktop running Xubuntu 14.04 , but I'd like to set it to "pause" for about 30 seconds on login before it starts. I've got it added to the 'Session and Startup' 'Autostart Applications' section as the command:

sleep 30; conky

But when I restart the machine, Conky never comes up...am I using the wrong command...?

Cheers and thanks! :)

---

### Post by vasa1 on 2014-05-01
Did you check using **pgrep conky** that conky isn't running at all? Sometimes, I found that conky likes to hide.
If it really isn't running what happens if you run **sleep 30s && conky**?

I'm on Lubuntu 14.04 and there I have a script to launch my autostart stuff:
```
#!/usr/bin/env bash

(sleep 3s && conky) &
(sleep 3s && tint2) & 
(sleep 3s && nm-applet) & 
(sleep 10s && cpu-usage-alert) &
(sleep 3s && /home/vasa1/.dropbox-dist/dropbox) &

```

---

### Post by RallyDarkstrike on 2014-05-01
I had tried the **sleep 30s && conky **command - didn't seem to do anything. However, I managed to find a way to get it to work, I created an executable file called conky-startup and somebody told me how to use a bash script to start conky from that file :)

Thanks though!

---

### Post by deadflowr on 2014-05-01
conky has its own pause command, so you don't need to use sleep
```
conky -p XX
```
XX being the number you want it to pause for.
Example 10 would be ten seconds.

---

### Post by vasa1 on 2014-05-03
> **deadflowr said:**
> conky has its own pause command, ...
Nice! Using that now.

---

### Post by WinEunuchs2Unix on 2014-11-21
> **deadflowr said:**
> conky has its own pause command, so you don't need to use sleep
```
conky -p XX
```
XX being the number you want it to pause for.
Example 10 would be ten seconds.

and a dead flower blooms with a unique answer.  haven't seen that one before.  nice.

EDIT: I just noticed your moniker "Accidental Geek" and your avitar holding an "Axe".  Not exactly an axiom i guess...

EDIT 2: Upon reboot and testing suggestion it doesn't work on this platform.  The font size defaults to 1920x1080 default font on the 17" screen (read unreadable) so reverting to the other best suggestion (in another thread) so far works best:

```

sh -c "sleep 10; conky;"

```

put this code in your startup applications menu option for Conky.

Also note dead flowers' suggestion also results in the Conky window starting up to the right side of the built-in display and not right side of the TV which is desirable and which manual invocation does.

...deblooming :P

---

