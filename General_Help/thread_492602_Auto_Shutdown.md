---
title: "Auto Shutdown"
date: 2007-07-04
forum: General Help
---

### Post by TruthlessHero on 2007-07-04
I searched briefly, so I apologize if it's posted somewhere else.

Is there any way to tell Ubuntu 7.0.4 to shutdown at X time? Third party maybe? I'm not that familiar with the features yet, so I apologize if it's a basic one.

---

### Post by carlx on 2007-07-04
I believe that you can do that by open a terminal and then insert:

```
sudo shutdown -h hhmm
```

Where you subsititute hhmm with the time when you want the system to go down.
You will then be prompted for you password

---

### Post by TruthlessHero on 2007-07-04
Hmm, that seemed to do number of minutes, but that will work. Many thanks.

Would you happen to know how to clear a shutdown that is running? I mean, I guess rebooting would, but I'd like to get rid of it and start a different one without rebooting.

---

### Post by McNils on 2007-07-05
If you are using carlx command you should be able to press Ctrl-C. Otherwise sudo kill XXX should work. XXX is the pid of the shutdown command.

---

