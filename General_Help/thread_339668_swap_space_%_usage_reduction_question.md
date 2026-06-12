---
title: "swap space % usage reduction question"
date: 2007-01-16
forum: General Help
---

### Post by craig.brisbane on 2007-01-16
Hello

I have a question regarding swap space % usage reducing after a period of time. I am using ubuntu 6.10. I have notice that naturally when running a large number of application the usage of the swap space increases in % .

However when I closed applications and the computer has  been idle for some time, the % of swap space used does not reduce. For example the computer was not used today while I was at work, with only one application open - Firefox 2.0.

Is the only way to reducing the % used rebooting?

Thanks for your help
Craig

---

### Post by Nonno Bassotto on 2007-01-16
In linux the ram management is a bit different from windows. The idea is that you paid for your ram, so you should use it. So when you close files, they remain cached, in order to be accessed more quickly if you need them later. This does not mean that you are consuming more ram, since the ram used for caching is freed as soon as another application needs it.

That said, I guess (but I'm not sure) it has the same behaviour with the swap. So it won't free it unless needed, but it won't use it either. In other words your swap space is occupied, but this doesn't mean that you are using it.

---

