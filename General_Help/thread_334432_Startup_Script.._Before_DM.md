---
title: "Startup Script.. Before DM"
date: 2007-01-08
forum: General Help
---

### Post by tumler on 2007-01-08
So basically I'm wanting to get my computer to load without a dm (gdm/xdm),
automatically load into a user account (through terminal) and run a script.

Could someone tell me how to auto login without gdm? 
And how I could run a script aftwerwards?

Thanks in Advance.

---

### Post by kerry_s on 2007-01-09
Here's what i did when i needed one-> [http://www.ubuntuforums.org/showthread.php?t=303319](http://www.ubuntuforums.org/showthread.php?t=303319)

---

### Post by tumler on 2007-01-09
Wow thanks alot.

I had searched on the internet and found lots of how-tos for dapper but none for edgy.

This how-to is extremely clear *bookmarked*
:D

---

### Post by tumler on 2007-01-09
Dam I just tried it out on my other comp and it didn't work.  :-? 
It's a Xubuntu Edgy system and when I completed the guide and restarted it just put me back into gdm. Tried uninstalling gdm but that stopped the computer loading.

Any advice?

---

### Post by djMoralita on 2007-01-09
Hi,

In line with this thread, I'm also trying to add a startup script after my ubuntu 6.10 server has boot up, I added it as a symlink in /etc/rcS.d/S91myscript.sh which points to /etc/init.d/myscript.sh

however, my server didn't boot up again, i tried recovery mode and it stalled in the S90 step which is the cleanconsole.sh part. 

I wonder where to add a startup script after it boot ups, I asked someone and he said that I add it at the end of an rc.local, I tried that before in a ubuntu desktop, but it didn't work, I will try it now in  a server, I wonder if it will it also crashed my install?

Cheers,

DJ

PS: I take this question back, the answer is very simple, I simply add it to my user's login script. ha ha ha, what was I thinking?

---

### Post by kerry_s on 2007-01-09
> **tumler said:**
> Dam I just tried it out on my other comp and it didn't work.  :-? 
It's a Xubuntu Edgy system and when I completed the guide and restarted it just put me back into gdm. Tried uninstalling gdm but that stopped the computer loading.

Any advice?

Double check you followed all the steps. Try it with out gdm installed. On all the systems i done it on i didn't have gdm cause i started from a base install.

---

### Post by tumler on 2007-01-09
Ok I got it working, and it works like a charm.

I found it was this command that wasn't working for me
```
sudo chmod -x /usr/bin/autologin
```
So I made it executable (through thunar)

Thanks for the help.

---

### Post by kerry_s on 2007-01-09
> **tumler said:**
> Ok I got it working, and it works like a charm.

I found it was this command that wasn't working for me
```
sudo chmod -x /usr/bin/autologin
```
So I made it executable (through thunar)

Thanks for the help.

Glad you got it working ;)  It always worked for me so i couldn't even think of what might have gone wrong. I fixed the how to, changed it from " sudo chmod -x /usr/bin/autologin " to " sudo chmod +x /usr/bin/autologin " Guess it was just a type O from my fat fingers :)

---

