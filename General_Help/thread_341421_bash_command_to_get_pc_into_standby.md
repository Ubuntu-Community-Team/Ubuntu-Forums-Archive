---
title: "bash command to get pc into standby?"
date: 2007-01-18
forum: General Help
---

### Post by thor918 on 2007-01-18
is there any command that can be used from the terminal to get pc to goto standby?

---

### Post by JamieC on 2007-01-18
Hm, you could try the following (where <time> is the time to suspend until and can either be a timer (+1:00 - 1 hour) or a time (9:00 - 9AM):
```

apmsleep <time>

```

---

### Post by thor918 on 2007-01-18
hi there. Thanks alot for your comment.
it seems to work. but what if you want it to not have a timed sleep. 
just sleep until someone tries to power it up again.

I'm looking at the documentation here:
[http://linux.about.com/library/cmd/blcmdl1_apmsleep.htm](http://linux.about.com/library/cmd/blcmdl1_apmsleep.htm)

haven't tested it yet:
-w, --wait 
Wait indefinitely for the time leap.

---

### Post by JamieC on 2007-01-18
Yeah, sorry about that, the -w parameter does not do that in Ubuntu:
> 
       -w percent, --warn percent
              When  the  battery  is not being charged and the battery content
              falls below the specified percent of capacity, and no such event
              has yet occurred in the current discharge cycle, apmd will log a
              warning at the ALERT log level to syslog(2) and generate  a  LOW
              BATTERY event.  If the -W or --wall option was given, the daemon
              will also use wall(1) to alert all users of impending doom.  The
              default  warning  level  is 10.  Use a negative value to disable
              this feature.


---

### Post by thor918 on 2007-01-18
where did you take that quote from?
well it seems the computer sleeps indefinitely no matter what I do so it would work perfect for me ;)

---

### Post by JamieC on 2007-01-18
I typed "man apmsleep" in terminal.

It's probably possible to achieve what you want to do but I don't have support for AMP compiled in my kernel. Therefore I'm unable to test out commands before posting them to ensure they work correctly.

Take a look at the manual for "apmd", that'd be your best bet:
```

man apmd

```

Sorry I'm unable to help you any further.

---

### Post by thor918 on 2007-01-18
in my man page it shows w = wait.
strange. we probaby run different versions then..

---

