---
title: "User Accounts tool (in system settings) won't start"
date: 2014-01-21
forum: General Help
---

### Post by Jamie_Dow on 2014-01-21
Hi,
I've often installed Ubuntu (and other distros) and never had this problem - very odd, and I can't fathom what the issue is.
A little googling and searching round these forums fails to locate anyone who's encountered the same.

Just put 13.10 on a desktop machine, from the DVD image. All went pretty smoothly.
I set up 1 user at install, so now want to add further users.
I go to System Settings > User Accounts (double clicking).
The System Settings window (which should - if the User accounts tool actually opened - then be behind the active user accounts window) goes grey.
Nothing happens.
The system as a whole isn't frozen. I can cycle between windows using Alt+Tab. If I choose Alt+F4, I get a window saying that the window "System Settings" is not responding, and I can force quit. It's as though it's somehow perhaps in the middle of something or even somehow expecting some input from me (I've tried typing in the password, in case there was some invisible window expecting the admin password - nope, it's not that).

I'd like the mystery solved, but most of all I'd like a tool that works for setting up users and groups.
I'm about to pass the machine on to someone else (not hugely techie), so I'd like there to be as much as possible just working.

Cheers, Jamie

---

### Post by DuckHook on 2014-01-21
Hi Jamie and welcome to the forums.

Leastwise, I assume from bean-count that this is your first visit.

What do logs tell you, especially auth.log? Also, can you set up through CLI (useradd, etc)? Is gksu installed?

---

### Post by Jamie_Dow on 2014-01-22
Hi, and thanks for engaging with this.
I can manipulate users using Kuser (run as root), which is a bit easier than doing it all via the command line. So, that's what I've done for now.

/var/log/auth.log doesn't show anything useful.
When I try to run the user accounts tool, when it gets stuck, when I force quit, nothing writes to auth.log 
Are there other logs I should expect to see something?

Cheers, Jamie
(not my first visit, but it's been a while, and I ended up forced to use a different id. I have done quite a bit of CLI stuff, and tinkering about, but I'm not a programmer, and knowledge has been picked up in an ad-hoc way, so what I know is quite patchy)

---

### Post by Jamie_Dow on 2014-01-22
OK, and now, having found out a bit more about what auth.log is, I don't really see why we would have expected to find useful info in there anyway. Maybe I'm missing something. Perhaps the idea was that if somehow the users tool was asking for some kind of authentication, and was force-quit from that point (assuming that it was somehow behaving as though it had presented a dialog box to the user, asking for a password, or something) - maybe *that* could have been expected to show up there.

I don't know. Is there some other log that would show that is happening when the users tool is started up (and gets stuck with the grey window behind it, etc.)?
Or what is going on when it is force-quit?

Grateful for all help / guidance / suggestions.

---

### Post by DuckHook on 2014-01-22
> **Jamie_Dow said:**
> OK, and now, having found out a bit more about what auth.log is, I don't really see why we would have expected to find useful info in there anyway. Maybe I'm missing something. Perhaps the idea was that if somehow the users tool was asking for some kind of authentication, and was force-quit from that point (assuming that it was somehow behaving as though it had presented a dialog box to the user, asking for a password, or something) - maybe *that* could have been expected to show up there.To my knowledge, invoking tools like user accounts, etc. involves elevating to root privilege and any elevation attempt will be logged in auth.log. What would have been useful was to see if there was a denial, which would provide a good clue about where to look next. There's nothing especially important or unique about auth.log, but when diagnosing, you've got to start somewhere and looking at authorizations for an app that deals in authorizations seemed logical. Syslog would also be a useful one to look at. Ubuntu comes with a log viewer that is very helpful.

As a rule, invoking apps graphically hides some useful output. Invoking from terminal is more informative when trying to chase down issues, as errors are directed to the terminal. Aside from looking in syslog, try launching app with terminal command:```
gnome-control-center user-accounts
```...and post output back to this thread.

---

### Post by Jamie_Dow on 2014-01-22
OK. Ran that as root and got this:

IBUS-WARNING **: The owner of /home/daniel/.config/ibus/bus is not root!
libv4l2: error getting pixformat: Inappropriate ioctl for device


I take it that the first of those is nothing to worry about.
But the second will be the thing that's causing the problems. But it means nothing to me!
Any ideas?

Cheers, Jamie

---

### Post by Jamie_Dow on 2014-01-22
OK. This has been good progress now, and the issue is - well, if not exactly "solved", certainly worked around adequately.
This relates to this bug: 
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1242367](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1242367)

And indeed, it does have to do with a TV card (which the machine has, but neither I nor the future user of the machine will require the use of).
So, the workaround at post #10 is perfectly usable for our purposes here.

Thanks, DuckHook, your assistance yielded the breakthrough! Much appreciated. (Wish they still had that thumbs up thing you could do years back on these forums, when a post had been really helpful!) Cheers, Jamie

---

### Post by DuckHook on 2014-01-22
> **Jamie_Dow said:**
> your assistance yielded the breakthrough!...and I didn't even *do* anything! You did this all on your lonesome, so kudos to your nose for solutions. By the time I got round to checking back on this thread, you had solved it yourself. It still floors me, though, how a TV card can bork an authentication module, but there you are.

Please mark thread "solved" with *thread tools* at top of page so that others looking for similar solutions will find this.

Good luck and Happy Ubuntuing!

---

