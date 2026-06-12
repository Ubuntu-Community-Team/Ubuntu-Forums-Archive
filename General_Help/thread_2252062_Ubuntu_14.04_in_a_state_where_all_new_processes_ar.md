---
title: "Ubuntu 14.04 in a state where all new processes are immediately &quot;Killed&quot; when started"
date: 2014-11-08
forum: General Help
---

### Post by mpthompson2 on 2014-11-08
Long time Ubuntu user, but I'm now running into a very weird problem where all new processes are immediately killed by the system.  I'm running Ubuntu x86_64 14.04 LTS with 8GB of RAM.

I working on builds of Chromium OS for an embedded system and part of the rather complex build processes is building tools in a chroot environment.  At some point during the build of the tools the builds will fail on me.  However, this isn't the issue.

Here is what is really weird.  Ubuntu is now in a state where I can't start any new program/processes at all -- not from the command line, not from a menu, not from a virtual console, not from anywhere.  Everytime I try to start any program in the shell, I see a "Killed" message.  An example is the following just trying to "ls" a directory:
```

mike@taurus:~$ ls
Killed
mike@taurus:~$
```

What's really frustrating is that I can't run anything when it gets in this state to diagnose the issue.  If I run "top" while putting the system in this state, I don't see anything obvious with the system resources such as to much memory consumption.  Once in this state my only choice is to power cycle to reboot the system and look for log messages in /var/log which doesn't turn up anything obvious.

I did suspect this was a ulimit problem and I did increase the maximum number of files that can be opened by a user from 1024 to 10240, but that didn't stop the problem.

Somehow Ubuntu is getting into a state where is just simply immediately kills any new process.

Any ideas on what the issue might be or how I might diagnose this?

---

