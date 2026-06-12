---
title: "Brightness controls on Lenovo B50 are reversed"
date: 2016-09-09
forum: General Help
---

### Post by trixi on 2016-09-09
I have a Lenovo B50 running Ubuntu 16.04 with Unity and the screen brightness controls are reversed, meaning when I'm trying to lower the brightness with the + function button, it will raise it and vice versa.
Anyone any ideas?

---

### Post by jeremy31 on 2016-09-09
Welcome to the forums.  Please post the result of ```
lspci -nnk | grep -iA2 vga
```

---

### Post by pqwoerituytrueiwoq on 2016-09-09
see post 2 of this thread to determine if this is something we can fix
[https://ubuntuforums.org/showthread.php?t=2336622](https://ubuntuforums.org/showthread.php?t=2336622)
it would probably be easer to make a new keyboard shortcut to run a script or program to adjust it, for example using <super> (windows logo key) instead of <fn>
you could use [xbacklight]("apt:xbacklight") for example
i have a script that can also adjust it, but it is on my laptop, I'll edit this post later with a link to it
edit: [http://pastebin.com/93WxFQdX](http://pastebin.com/93WxFQdX)

---

### Post by trixi on 2016-09-11
> **jeremy31 said:**
> Welcome to the forums. Please post the result of ```
lspci -nnk | grep -iA2 vga
```

Thank you!
The output of "lspci -nnk | grep -iA2 vga" is
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0e)
        Subsystem: Lenovo Atom Processor Z36xxx/Z37xxx Series Graphics & Display [17aa:3986]
        Kernel driver in use: i915

```


> **pqwoerituytrueiwoq said:**
> it would probably be easer to make a new keyboard shortcut to run a script or program to adjust it, for example using <super> (windows logo key) instead of <fn>
you could use [xbacklight]("apt:xbacklight") for example

That seems cool, but actually I don't even use brightness controls that much, it's more like an annoying little problem, an issue of "I want to fix this and make it work properly" so I'd really love to see if there's a way to fix it instead of a workaround.

---

### Post by scotty1212 on 2016-10-20
I have the same problem with my laptop.. It is a little of an annoyance and have been sticking up with it.

---

