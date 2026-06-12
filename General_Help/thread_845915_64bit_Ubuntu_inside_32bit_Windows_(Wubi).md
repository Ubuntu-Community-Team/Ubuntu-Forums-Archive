---
title: "64bit Ubuntu inside 32bit Windows (Wubi)"
date: 2008-07-01
forum: General Help
---

### Post by can8dnSix on 2008-07-01
Has anyone installed 64-bit Ubuntu inside 32-bit Windows? Please look at the "question" before posting anything back as I find it extremely annoying when people say things like... "well why would you want to do that?" The question is closed ended, unless you answer yes, to it, then add your findings to this. Thanks! xo!

---

### Post by ago on 2008-07-01
The version of windows is totally irrelevant. What matters is the CPU you have. If it supports 64 bits wubi will (rightly) try to install a 64 bit version of Ubuntu, unless you provide a 32bit ISO or run Wubi with the --32bit argument. Note that Wubi itself (the installer wizard) is 32 bit.

I say it is irrelevant because Ubuntu does not actually run inside Windows, it is only installed inside of the windows filesystem. I.E. Windows does not run when Ubuntu does.

---

### Post by can8dnSix on 2008-07-01
Awesome; and the disadvatage will obviously be running inside of Windows' filesystem. I suppose the next question will be this, if there is a software raid being used in Windows, will it be enabled prior to running Ubuntu? I guess I will find out. lol Anyway, thank you; just like playing with linux, it's fun. :)

---

### Post by can8dnSix on 2008-07-02
So, in short.. NO, it loaded but did not successfully load. Basically got the generic error for not loading lol. Anyway, cool.. thanks. Messing with another thing now. :) ~Resolved~

---

