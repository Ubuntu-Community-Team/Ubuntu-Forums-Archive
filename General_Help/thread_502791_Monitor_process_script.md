---
title: "Monitor process script"
date: 2007-07-17
forum: General Help
---

### Post by brent113 on 2007-07-17
Hi, i was wondering if someone could help me write a script.

I plan on running it on startup:  I would like it to start a process, and any time it crashes (closes) i would like it to be restarted as long as the computer's on.

Maybe something like calling ps -ef|grep processname every 10 seconds and if it's not running (only returns the grep process) then restart it.

Or am I barking up the wrong tree and there's a better way to do this?

Thanks!

Brent

---

### Post by kidders on 2007-07-18
Hi there,

One simple way of approaching your problem is simply to instruct an app to execute over and over again. For instance, **firefox || firefox** would launch a web browser & then relaunch it, in the event it exited abnormally. Something based around that idea would perhaps be the fastest way to achieve the effect you want.

On the other hand, your post kinda implies that you may prefer to keep the process and its monitor parallel. In that case, something along the lines of **if [ -z "`pidof $PROCESS`" ]; then $PROCESS &>/dev/null &; fi** (given an appropriately defined PROCESS) would do the trick ... in a loop, as you suggest.

Of course, depending on what the process we're talking about is, it might be appropriate to do a few additional things, for instance...[LIST]
[*]Some things can leave a mess behind when they die unexpectedly. You might want to do some housekeeping before restarting whatever it is.
[*]Processes typically exit abnormally when a PC is being shut down. It might be a good idea to verify that a shutdown isn't in progress before blindly relaunching your process.
[*]One thing that's nice about the serialised approach I mentioned first is that you can measure the time it took for your process to die. You might, for instance, want to reconsider a relaunch if multiple crashes occur very close together, to avoid upsetting your box.[/LIST]

---

