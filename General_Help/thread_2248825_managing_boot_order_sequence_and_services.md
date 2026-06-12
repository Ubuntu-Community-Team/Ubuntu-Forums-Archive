---
title: "managing boot order sequence and services"
date: 2014-10-17
forum: General Help
---

### Post by mscrano on 2014-10-17
Hi I have a question regarding the ability to control the order in which services come up at boot time.  I have written a script that I run on reboot via cron, the script requires access   to an NFS mount, it should also be run before another service (Sun grid engine) in my case.  Is there a way that I can get NFS to come online before cron and delay execution of SGE until my script has completed.  Currently with the default boot order my NFS mount is unavailable when the script attempts execution.  Thanks in advance to any advice that you can provide!

---

### Post by TheFu on 2014-10-17
First, welcome to the forums.

In the old days (pre-14.04), I'd say - this is trivial and easy. Just setup the init.d/ order using the numbers in the different rc?.d/ directories.
 .... 01* comes before 99*. **update-rc.d** does this, or you can do it manually following the existing pattern with symlinks already there.

Today, things around service initialization are changing ... or have or will change shortly.  I don't know the status, sorry.  A change to systemd is the reason.  My LUG gave a talk about systemd last night, but I had a different meeting to be at, so I missed it.  Ubuntu 14.04 has some systemd stuff - I don't know how much.  The great thing about systemd is that startup dependencies like this are part of it. I don't know how to do that for custom stuff and it is unclear to me how shutdown dependencies are addressed, if at all.

Plus the main guy behind systemd is the guy that screwed pulse-audio for everyone. For many years, the first thing I did on every box was purge pulse audio. Hopefully this will work better.  I've read that gnome already has dependencies for systemd stuff. That doesn't make me happy at all.

Sorry I don't know more.

So ... if the system is running 12.04 or 10.04 - just do the update-rc.d in the old way.  If 14.04 ... uh ... I don't know. Clearly, anyone running a server wouldn't run any other version of Ubuntu.

---

### Post by mscrano on 2014-10-17
Well I was looking at the startup scripts in /etc/rc2.d but cron is not in there, because it is an upstart job, so I wasnt sure how to change when that executed. I am working on 12.04 Thanks for the warm welcome.

---

### Post by TheFu on 2014-10-17
I'm confused.  

Cron is starting too quickly on your system - before networking, then NFS mount, so you want to delay it?

If you run something at reboot - you can have it wait.
If you run something with cron - then it will run at the appointed time or frequency.  

Why not just have the script see if the NFS mounted storage is there and if it isn't, exit until the next crontab time? If the period this thing is supposed to run is every 5 min, that should be fine, but I guess it depends on the specifics.

It sounds to me like starting this up via cron is NOT the best answer.  Would making a nominal init script not work?

---

