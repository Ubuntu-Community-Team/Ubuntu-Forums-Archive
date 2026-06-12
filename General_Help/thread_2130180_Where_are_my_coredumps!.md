---
title: "Where are my coredumps?!?"
date: 2013-03-28
forum: General Help
---

### Post by ArlieS on 2013-03-28
I'm running Ubuntu 12.10 desktop. I'm attempting to use it as a convenient platform for software development. My program crashed with a SEGV. It claimed "Segmentation fault (core dumped)". There was no core. 

A little digging around gave me:

```

$ cat /proc/sys/kernel/core_pattern
|/usr/share/apport/apport %p %s %c

```

That explained a lot - Ubuntu desktop isn't intended for software developers. Fair enough. 

My next problem was how to do

```

# echo "%e.core" > /proc/sys/kernel/core_pattern

```

using sudo.

I solved that via 
```

# sudo xterm

```

Fine, now I have 

```

$ cat /proc/sys/kernel/core_pattern
%e.core

```

But when my program SEGV's, I get "Segmentation fault" rather than "Segmentation fault (core dumped)". Unsurprisingly, there is no core.

At this point I lost patience. I'm going to do my debugging on a Scientific linux server rather than on my Ubuntu desktop.

But for future reference - what other helpful customizations do I need to undo to do development on a Ubuntu 12.10 desktop, and how do I prevent the inconvenient settings from coming back when I reboot, or when I instal Ubuntu bug fixes?

---

### Post by ArlieS on 2013-03-28
I found part of it. 

Ubuntu has helpfully defaulted the RLIMIT_CORE to 0. 

To fix this, try:

```

$ulimit -c unlimited

```

You probably have to do that in the specific window where you intend to do your debugging, since I believe it's a process attribute [inherited by a process' children], not a user attribute.

---

### Post by rnerwein on 2013-03-28
> **ArlieS said:**
> I'm running Ubuntu 12.10 desktop. I'm attempting to use it as a convenient platform for software development. My program crashed with a SEGV. It claimed "Segmentation fault (core dumped)". There was no core. 

A little digging around gave me:

```

$ cat /proc/sys/kernel/core_pattern
|/usr/share/apport/apport %p %s %c

```

That explained a lot - Ubuntu desktop isn't intended for software developers. Fair enough. 

My next problem was how to do

```

# echo "%e.core" > /proc/sys/kernel/core_pattern

```

using sudo.

I solved that via 
```

# sudo xterm

```

Fine, now I have 

```

$ cat /proc/sys/kernel/core_pattern
%e.core

```

But when my program SEGV's, I get "Segmentation fault" rather than "Segmentation fault (core dumped)". Unsurprisingly, there is no core.

At this point I lost patience. I'm going to do my debugging on a Scientific linux server rather than on my Ubuntu desktop.

But for future reference - what other helpful customizations do I need to undo to do development on a Ubuntu 12.10 desktop, and how do I prevent the inconvenient settings from coming back when I reboot, or when I instal Ubuntu bug fixes?
hi
for permant setting you can use /etc/security/limits.cof. there you can set the value for core as you want. have a look at: man limits.conf
ciao

---

