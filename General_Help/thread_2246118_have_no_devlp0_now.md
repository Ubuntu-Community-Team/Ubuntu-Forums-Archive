---
title: "have no dev/lp0 now"
date: 2014-09-28
forum: General Help
---

### Post by sam_baker2 on 2014-09-28
hello


I use to could plot a file to my plotter with this command:
```

cat plot1 > /dev/lp0

```

now I get this when I try the command:
```

cat: /dev/lp0: No such file or directory

```

Upon looking under dev/  I see that lp0 is not there.
I have a lp0 under dev/usb , but it has a "x" in the little icon just to the left of "lp0"

the last I plotted was about a year, so I think that in the process of updates,
something might have happened.

I use 12.04 

Anybody have any idea as to how to get lp0 back?

Thanks

---

### Post by sam_baker2 on 2014-10-12
bump

Might anybody know about this?
My USB port has a cable hooked up to it that goes to the parallel port on my big HP plotter.
I use to could plot a drawing with this command:

```
  cat plot > dev/lp0

```
but now  I see that there is not any "lp0" under /dev.
I have a "lp0" and a "lp1" under /dev/usb, but they are "X"ed out.

Any help appreciated. I need this for my work.

---

