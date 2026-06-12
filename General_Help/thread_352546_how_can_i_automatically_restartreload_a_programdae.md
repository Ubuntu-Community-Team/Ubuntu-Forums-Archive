---
title: "how can i automatically restart/reload a program/daemon if it crashes?"
date: 2007-02-03
forum: General Help
---

### Post by BrowneR on 2007-02-03
I have a slightly buggy C program which I like to keep running in the background for monitoring purposes. Occasionally it quits randomly without error (and i dont have the skills to debug it :p).

Is there a way I can launch it so that it will be restarted automatically if it crashes?

I suppose I could create a script that monitors the output of ```
 ps -a | grep "program name" 
``` and relaunches it when there is no match but there must be a better way...?

---

### Post by lloyd_b on 2007-02-03
> I have a slightly buggy C program which I like to keep running in the background for monitoring purposes. Occasionally it quits randomly without error (and i dont have the skills to debug it ).

Is there a way I can launch it so that it will be restarted automatically if it crashes?

I suppose I could create a script that monitors the output of
Code:

```
ps -a | grep "program name"
```

and relaunches it when there is no match but there must be a better way...?

Create a shell script (in this example, "keepalive.script"):
```
#keepalive.script
program_name
keepalive.script
```

Then run the shell script in background.  program_name will run, and when it quits, the script will recursively call itself, running program_name again.

Note: This assumes that program_name is NOT a true daemon.  If it's actually a daemon, then once the program is launched it will immediately return to the script, and you're going to wind up with a zillion copies of it running at once!.

If it is a true daemon you can use the system's init utility to accomplish the same thing.  I can't provide directions for this, though, as it depends on which version of Ubuntu you're using - Edgy uses "upstart", which is controlled via "/etc/event.d" entries, while older versions use "init", which is controlled via the "/etc/inittab" file.

---

### Post by BrowneR on 2007-02-03
thats great, so neat and simple i didnt even consider it :p
thanks!

---

### Post by slAoD on 2007-03-22
anyone knows how to do this in upstart?? in /etc/inittab in previous versions of ubuntu was easy (just one command), but what about upastart?

---

### Post by lloyd_b on 2007-03-22
> **slAoD said:**
> anyone knows how to do this in upstart?? in /etc/inittab in previous versions of ubuntu was easy (just one command), but what about upastart?

Fair warning - I am NOT all that familiar with upstart!

Here's what I *think* will work:
1.  Copy one of the "tty..." entries in "/etc/event.d" to a new name (let's call it "myprog").
2.  Edit "myprog", replacing the line "respawn /sbin/getty 38400 tty1" with the command you want to run
3.  In the terminal, type "sudo start myprog".

You may or may not want to edit the various "start on runlevel..." lines - depends on what your program is trying to do.

If you want to stop that process from respawning, "sudo stop myprog".

Lloyd B.

---

