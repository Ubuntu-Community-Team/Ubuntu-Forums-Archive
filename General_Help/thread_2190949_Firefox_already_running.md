---
title: "Firefox already running?"
date: 2013-11-30
forum: General Help
---

### Post by ML7rcEx on 2013-11-30
I am running Lubuntu 13.10 and my problem is when i close Firefox and then sometime later decide to use it again a message appears stating that Firefox is already running (when it is not) and to close it first. The only way i can get Firefox running again is to re-boot the machine. I have had this problem before with Ubuntu and on a different machine. Then i had to open a terminal and type some code to prevent this from happening. Could someone help please.

---

### Post by Bucky Ball on 2013-11-30
Open a terminal and type this code:

```
killall firefox
```

That should get rid of it.

Does it start doing this every time you open Firefox and then close it again, the error comes up it is already open when you try to launch it again?

---

### Post by ML7rcEx on 2013-11-30
Big thanks for the help Bucky Ball

---

### Post by paul.drover on 2014-03-10
Hmm. I'm running 13.10. Since the latest firefox update (v27.0.1) everytime I close firefox, it leaves behind an instance that is not attached to any window I have open. So I get the "already running" error when I try to restart it. I resport to a command line ps grepping for firefox (it's always there) then kill -9 the pid. This makes it go away... until next time. Then the same thing all over again. This is getting rather tired. Is this a known issue? Does anyone know of a perminent fix?
Thanks all,
Paul.

---

### Post by Bucky Ball on 2014-03-10
This thread hasn't been touched for months. You are asking a different question than the OP (who seemed to want the command to kill Firefox), but have a read of post #2 and if that doesn't work for you, please post a new thread with more detailed description of your issue. 

Thanks.

*Thread closed.*

---

