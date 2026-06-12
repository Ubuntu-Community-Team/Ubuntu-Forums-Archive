---
title: "Hardy Rythmic Freezing"
date: 2008-04-29
forum: General Help
---

### Post by phynix on 2008-04-29
Ok firefox and pidgin will randomly freeze for five seconds, and then will unfreeze and work normally. This cycles over and over. I watched it on task manager and it firefox goes from no cpu usage to 19 over and over. The only thing I have done is compiled a new kernel which I am not using, but thought I should mention it just in case.

---

### Post by chenel on 2008-04-29
What kind of machine are you using?  I had a Dell Inspiron 8100 that used to do that under linux.  After days of googling, I finally discovered that the problem was the CPU frequency scaler (speeds up and slows down processors that can do that based on load)...  powernowd just didn't do it properly for some reason.

I uninstalled powernowd and installed cpudyn and, presto! - everything worked fine.

Though, come to think of it, it didn't matter what programs I was using.  Dunno if this will help you or not.

---

### Post by phynix on 2008-04-30
I have dell 1420n as well but its running 64 bit.Its odd I uninstalled it then installed it again with two in case things didn't work out and now its running fine. Weird.

---

