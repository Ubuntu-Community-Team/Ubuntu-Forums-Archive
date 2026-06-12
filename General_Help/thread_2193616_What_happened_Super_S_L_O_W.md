---
title: "What happened? Super S L O W"
date: 2013-12-13
forum: General Help
---

### Post by BeeSharp on 2013-12-13
Ubuntu 12.04 was running great on a Dell Dual CPU 2.16 ghz with 2 gb ram for a couple years. Something happend within the last couple days that has made the system super slow.

I looked at the system monitor and just scrolling the mouse a little bit took both cpu's to 100%. Just typing this I'm way ahead slowly typing to the display!!

I've happily used ubuntu for several years, but I'm really a beginner when it comes to nuts and bolts of the system.

Any suggestions would be welcome!
Thanks
Jim

---

### Post by VMC on 2013-12-13
Open a terminal (Ctrl+Alt+T), then type top. What program is using up the %CPU ?

---

### Post by stinkeye on 2013-12-13
I would also check you gfx .....
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by BeeSharp on 2013-12-13
firefox, Xorg & compiz are the cpu hogs

When I ran the gfx everything came up "yes"

Thanks
Jim

---

