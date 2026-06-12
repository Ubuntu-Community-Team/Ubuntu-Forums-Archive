---
title: "Intermittent gnome log-in problem"
date: 2007-12-01
forum: General Help
---

### Post by darrylmcginnis on 2007-12-01
I'm having an intermittent problem with 7.10 (Gutsy) that I haven't been able to find any message threads quite the same as what I'm experiencing...

Generally I leave the computer on all the time and everyone in the family logs in and logs out as needed with their own user ids.  What I've found is that if the computer sits for an extended period of time (several hours) at the graphical login screen, the likelihood of the problem manifesting itself is increased. After entering the user and password, the screen will go to the solid light tan color with a mouse pointer, it plays the login sound completely, but the Gnome desktop never appears - the system is not frozen however - mouse moves and I can switch to another tty.  (Remember this is an intermittent problem - After a fresh boot or recent computer usage, the desktop normally appears within 5 seconds or so after entering the password).  I saw several threads about a "long time to login", but somehow I think that if it works normally in less than 10 seconds; then when the problem occurs and I let it sit on the tan screen for over an hour -- I don't think that's the issue.. The message threads also seemed to indicate that for them it was an all-time-time issue.  

I've also read that I should look in .xsession-errors to see what errors are encountering during that time-frame.  I've done Ctrl-Alt-F1 to log into another terminal session while it is "hung" and found the last couple lines are:
[FONT="Courier New"][B]/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/roo:/tmp/.ICE-unix/####[/B][/FONT]     
(where #### is a variable four-digit number (Process ID?)
...so there really isn't any error reported here in my case.

Crtl-Backspace resets the session back to the login screen, but any further attempt to login winds up with the same results...

After a reboot, there is no problem logging in. (Until the system has sat at the login screen for a good while).

Looking forward to hearing from anyone with some ideas on how to fix this...

Darryl

---

