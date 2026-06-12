---
title: "cpu scheduling"
date: 2007-05-25
forum: General Help
---

### Post by Big_Croc7 on 2007-05-25
Hi, is there an (easy!) way to limit the amount of processor time that can be devoted to either:
a. a certain process,
or b. a certain user?
The reason is, I'm want to run some long-running computation processes, but don't want my pc to get hot and the fans to work hard - that makes it noisy! ;-)
Either option is fine, I guess b. might be slightly more useful (and possibly easier to implement?)
I assume there is a way to do this, but I've searched and can't find anything on it.

---

### Post by mbradlcu on 2007-05-25
maybe just throttling the cpu would work if it's available with your hardware... 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by Big_Croc7 on 2007-05-26
Don't think it is available - I get 'no such file or directory', I'm pretty sure it isn't.

Ideally I'd be able to throttle it per user, but throttling it overall would be ok too.  Underclocking in the bios isn't an option though, unfortunately (it's multiplier locked).

---

### Post by mbradlcu on 2007-05-27
humm, well 'nice' kinda does what you need but (I believe) it's only effective if the system is under full load,, check out  [http://einstein.phys.uwm.edu/forum_thread.php?id=2778](http://einstein.phys.uwm.edu/forum_thread.php?id=2778), it's a proggy called boinc,
sorry I can't help out more.

---

### Post by Big_Croc7 on 2007-05-27
Thanks for the info.  Nice dosen't really work the way I want - I can set the process to nice 19 or whatever, but as you say, it only works if the system is under load; if there's nothing else running it will still take 100% cpu and make the fans turn on.  The command above about throttling didn't give me anything, but searching for throttling instead found this guide [http://blog.heuristicdesign.co.uk/archives/2005/06/12/throttling-the-cpu-with-linux/](http://blog.heuristicdesign.co.uk/archives/2005/06/12/throttling-the-cpu-with-linux/)
that works.  Which kind of does what I want, although it's a bit clunky.  I'm going to go with it for now though, unless anyone knows a better way?  Ideally, I'd have it limited for one user, which would run the computation, but leave the full power available for other users if I want to do anything else.
thanks for your comments, at least they've led me to a partial solution!

---

