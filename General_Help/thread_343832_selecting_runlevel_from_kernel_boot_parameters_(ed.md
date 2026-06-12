---
title: "selecting runlevel from kernel boot parameters (edgy / upstart)"
date: 2007-01-22
forum: General Help
---

### Post by edp on 2007-01-22
Hey everyone. On all inux versions that i've ever used, with a sysv style init, you could give a runlevel number as the last argument to init, and that would set the runlevel that you boot to for that session.

Is there any way to do that (besides the single-user runlevel that /etc/event.d/rc-default provides for specially) so that I can select a GDM runlevel or a server runlevel without X11 at boot time?

The old way doesn't seem to work. I've added 3 to my kernel parameters at the end, and the kernel dutifully passes this to init, and yet this does not convince init to select that runlevel:

```

$ ps 1
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:03 /sbin/init persistent 3

$ who -r
         run-level 2  2007-01-22 01:23                   last=

$ runlevel
N 2

```

I hope there's a way to do this, and that adding new init boot parameter conventions is not left as an exercise to the reader.  The upstart scripts still refer to this as the "default" runlevel, which implies that you can change the default somehow, hopefully in a kernel parameter.

Thanks,

Ed

---

