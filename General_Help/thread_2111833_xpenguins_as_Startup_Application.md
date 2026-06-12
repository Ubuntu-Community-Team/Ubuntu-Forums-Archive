---
title: "xpenguins as Startup Application"
date: 2013-02-03
forum: General Help
---

### Post by nuk28 on 2013-02-03
I'm trying to add xpenguins to the Startup Applications (power button -> Startup Applications in 12.04). I've put "xpenguins -n 12 -d :0.0 --all" into the Command area for Startup Programs, but xpenguins doesn't show. When I boot up my computer and log in, I can see the penguins for a little bit, but then once everything starts up they disappear. I can open the System Monitor and see xpenguins still running, but I can't see the penguins on my desktop.

I think the problem is because the penguins are getting sent to the wrong display, the display that's there before the normal display appears (hence attempting to use the -d option). Perhaps there's a file somewhere that I can add this command to for loading once the window manager is fully loaded?

---

### Post by nuk28 on 2013-02-24
To fix this, I added a delay to the program so it starts up after 5 minutes. To do that, I used this command:```
sh -c "sleep 5m && xpenguins -s -n 5 --all"
```
Incidentally, I found another cool program called oneko. I run it with the -tomoyo parameter. It's especially cool because if you make Tomoyo (or any of the oneko characters) run into any of the xpenguins characters, it kills them!

---

