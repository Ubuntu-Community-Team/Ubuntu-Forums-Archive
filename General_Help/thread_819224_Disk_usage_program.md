---
title: "Disk usage program"
date: 2008-06-05
forum: General Help
---

### Post by Tom--d on 2008-06-05
Is there a program which shows the disk usage and what files are being used etc.

I remember, back when I had vista, there was a program which showed you the disk usage and whats being used etc etc.

Would like it to be in the repos,

Thanks,
Tom

---

### Post by Pjotr123 on 2008-06-05
It's already built-in.  :-)

System - Administration - System monitor

Tab: File systems

(ignore the gvs-fuse-daemon, that's a double count).

Greeting, Pjotr.

---

### Post by mrMango on 2008-06-05
That's one way to show it. Another, more useful, utility is found under Applications -> Accessories -> Disk Usage Analyzer

And of course you can always use [FONT="Courier New"]du[/FONT]. [[FONT="Courier New"]man du[/FONT]]("http://linux.die.net/man/1/du")

---

### Post by Tom--d on 2008-06-05
Yeah. I know them :)

What I mean is:

It shows the percentage of the usage.
What file(s) is being used by the hard drive.
etc etc
Basically a monitor but shows those things.

---

### Post by mrMango on 2008-06-05
Oh, in that case I would install atop.

```
sudo apt-get install atop
```

After you start atop from the terminal, hit Shift+D to sort by disk usage.

---

