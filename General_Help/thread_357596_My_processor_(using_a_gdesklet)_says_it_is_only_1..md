---
title: "My processor (using a gdesklet) says it is only 1.596GHz, but it is a E6600 (2.4GHz)?"
date: 2007-02-09
forum: General Help
---

### Post by presbp on 2007-02-09
I have a Core 2 Duo and it is a E6600 (2.4GHz dual core) but I am using the side candy gdesklet to show CPU usage and it says it is 1.596Ghz at the top of the applet but if I mouse over the CPU image it shows me the CPU name and says it is a dual-core 2.4GHz-and it's load is about 7% on average.. It usually stays about 4% in Windows when not playing games (3D games) 
Something odd going on?

---

### Post by neilp85 on 2007-02-09
What's happening is processor scaling. Since you're not doing any CPU intensive tasks, there is no need to run at it's full speed. If you do something that requires lots of cycles like compiling a large library you should see it jump to the full 2.4GHz

---

### Post by nickoli_02 on 2007-02-09
If you're on a desktop and you don't want your processor to be throttled down you can set the scaling governor to "performance", though I think you may need to remove powernowd and install cpufreqd using apt-get.

---

