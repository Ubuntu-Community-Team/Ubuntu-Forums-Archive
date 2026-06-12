---
title: "Failed to start X server from liveCD"
date: 2006-09-10
forum: General Help
---

### Post by Fibonacci on 2006-09-10
Hello,

I'm trying to boot Ubuntu from the liveCD, and I get this error message on a text console:
```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes>    <No>
```

Before I'm done reading that, more error messages appear on the screen, overwriting the one I had, and even overwriting each other, so I cannot read them. When I finally get an interactive shell (with broken text lines, though), I try to startx, and get a loooong error message of which only the end can be read:
```
Fatal server error:
No screens found.

XIO:   Fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
```

Now, the other threads regarding this issue advise the users to get the nonlive CD - however, there's no way on Earth I'm installing Ubuntu without having first thoroughly tested the liveCD.

I'm using an nVidia GeForce 5200FX video card, but neither Knoppix 4.0.2 nor Fedora Core 5 Bordeaux have any problem with it. What else can I do about this problem?

Thanks in advance,

-Fibo

---

### Post by Fibonacci on 2006-09-10
Just tried it from another computer using the built-in video card (don't know which one would that be, but I'm sure it ain't an nVidia) and I don't have such problems. Ubuntu liveCD starts normally.

---

### Post by Fibonacci on 2006-09-10
Update: It works using safe graphics mode - in fact I'm posting from Ubuntu right now.

Can I make "normal mode" work too? Or am I forever doomed to safe graphics?

Thanks again,

-Fibo

---

### Post by Niamor on 2006-09-11
Well, if you use only the live cd then yes, safe graphics mode is the only option. If you install ubuntu to your hard drive you will then have the possibility to install nvidia-glx, proprietary drivers, which works much better :)

---

