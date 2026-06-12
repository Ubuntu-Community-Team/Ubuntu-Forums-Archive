---
title: "ksoftirqd/0 using 30% CPU on idle..."
date: 2007-11-17
forum: General Help
---

### Post by CD Baric on 2007-11-17
AMD Athlon 2000+
775 MBytes
VIA Apollo chipset
nVidia MX 400 video card

Am experiencing a continuous 25-30% CPU usage for ksoftirqd/0 according to top.

Machine will not run any "Visual Effects" despite running an nVidia video card with nVidia restricted drivers.

Please Help!

Thank you.

Bar

---

### Post by CD Baric on 2007-11-23
Come on people, I need some asssistance here.

I can run Slax 6.0 rc6 on this box with no problem so it has to have something to do with the Ubuntu kernel.

If you can't help, perhaps direct me to which forum to try.

Bar

---

### Post by skymera on 2007-11-23
can you try top in the terminlal?

```
 top 
```

that should say whats using your processing power.

whhat nvidia driver have you got installled? how did you install them?

---

### Post by CD Baric on 2007-11-23
As I stated in message one, "top" indicated that "ksoftirqd/0" is using 30% CPU.

I also stated in the first message that I was running Ubuntu nVidia restricted drivers.

ksoftirqd is a kernel thread that runs when the machine is under heavy soft-interrupt load.

The same load is present when running as root in command line mode when idle.

The problem has to be something in the custom Ubuntu kernel - I am looking for a solution here.

Bar

---

### Post by nilezon on 2007-12-01
I'm having the same problem. No solution yet :(

Edit:
Solution found. I am using a WinFast 2000 tv card.
More info:
[http://ubuntuforums.org/showthread.php?t=584221](http://ubuntuforums.org/showthread.php?t=584221)

---

