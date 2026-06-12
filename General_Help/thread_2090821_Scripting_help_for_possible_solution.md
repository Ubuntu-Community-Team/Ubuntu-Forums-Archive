---
title: "Scripting help for possible solution"
date: 2012-12-03
forum: General Help
---

### Post by dishe on 2012-12-03
Hey guys and girls,
I was wondering if anyone could help me figure out out how to write a script that does the following:

Upon initial log in, automatically log off and log on again. Obviously I'd only want to do this once in order to avoid an infinite loop. Why do I want to do this? 

To avoid the bug I'm finding here:
[http://ubuntuforums.org/showthread.php?t=2081855](http://ubuntuforums.org/showthread.php?t=2081855)

I've found that logging out and logging back in prevents the mouse bug from happening anymore, so I end up having to do this once per session. Until I figure out how to fix that particular bug for good, my routine is to immediately log out after booting up the computer and logging back in. It seems like something I should be able to automate, right? I'm just not sure how to go about doing it, and more importantly how to make it only does this the first time and doesn't get stuck in a loop doing this forever.

---

### Post by Habitual on 2012-12-03
I've started threads many times that just wound up being me talking something out, and resolving it :)

A quick test:
Create a new user and login as that user and see if the problem persists?

Please let us know...

subscribed with interest...

---

### Post by dishe on 2012-12-05
> **Habitual said:**
> I've started threads many times that just wound up being me talking something out, and resolving it :)

A quick test:
Create a new user and login as that user and see if the problem persists?

Please let us know...

subscribed with interest...

Thanks!

I tried creating a new user, same thing. The mouses loses control of the window by context. A quick CTRL-ALT-DEL and space bar to hit OK to log off (since the mouse can't actually touch it), then log back in and it's fine. Problem doesn't come back unless I shutdown and start up from a cold boot again next time. I actually find myself leaving this on Standby a lot more often for that reason!

Bizzare. I want to fix it, but if not at least I should be able to script this to happen automatically, right?

---

### Post by Habitual on 2012-12-05
[QUOTE=]...Upon initial log in, automatically log off and log on again....[/QUOTE]

You don't login auto-magically to the desktop do you?

---

### Post by dishe on 2012-12-05
> **Habitual said:**
> You don't login auto-magically to the desktop do you?

Nope, have to sign in with password. Why?

---

### Post by Habitual on 2012-12-05
It's been problematic in the past.
Anything obvious in ~/.xsession-errors?

---

### Post by dishe on 2012-12-05
> **Habitual said:**
> It's been problematic in the past.
Anything obvious in ~/.xsession-errors?

Not sure. I'm rusty with my linux and trying to learn fast. 
Here is my current .xsession-errors file, as I log in when the problem occurs. 

This was actually quite difficult to do, as the bug described earlier prevents not only mouse context from changing active windows, but even alt-tab is useless. I was afraid if I actually logged out and back in to eliminate the bug, the errors log would be cleared. Is that how it works?

Anyway, I put it up on pastebin:
[http://pastebin.com/uDanw766](http://pastebin.com/uDanw766)


EDIT: I just looked it over and noticed the message about Rayman Raving Rabbids ISO being missing. Haha- I'm surprised that is showing up as a problem, it was part of an experiment I was doing with my kids. The mouse-context bug existed from the day I installed Ubuntu (in fact, it even existed on the live CD), so I think I can safely say that error is irrelevant.

---

### Post by dishe on 2012-12-14
Ok, so putting aside whatever is causing the problem in the first place (that was the purpose of my first thread), I'd like to see if I can automate a workaround here.

A simple log out, log back in seems to resolve it. But I have to do this everytime I boot from the laptop being off. 

How can I automate this process? Have it log off and back on upon initial boot?

---

### Post by dishe on 2013-02-05
My temporary solution which has been working well so far, is to hibernate the computer instead of ever shutting down. That way, it always wakes up to a desktop environment that has already used the above workaround (log out and back in) to fix the mouse context bug. 

I just really wish someone could help me get to the bottom of whatever this is in the first place. *sigh*

---

### Post by rnerwein on 2013-02-05
> **Habitual said:**
> I've started threads many times that just wound up being me talking something out, and resolving it :)

A quick test:
Create a new user and login as that user and see if the problem persists?

Please let us know...

subscribed with interest...
hi
what i read in the threads the last time is: that guy isn't alone. first i ain't have this problem. but i can tell you what i will do when i have this problem.
you must have the requirement to login via ssh when the terminal  showes the login-screen  (or something else). you must be valid to get super-user wrights. then (in a terminal ) run: ps -ef | grep light (or the desktop manager you use).
ok - now you get the PID and PPID of the processes which manage your login.
now start two "ltrace" commands each one in the background "&". 
you have to start it with: ltrace -ff -o light.trc -p PID of lightdm and ltrace -ff -o X.trc -p PID of the X-server.
i know that's a huge output in the created files. send this files to the developer (they want't be amused). but if anybody want to fix the problem he will have a eye on the files.
why "ltrace" - strace gives you only the systemcalls (in ltrace you can even see something like a buffer-override and the function where it happened).
cheers

---

