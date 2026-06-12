---
title: "I messed up my frequency scaling..."
date: 2007-07-21
forum: General Help
---

### Post by msandoy on 2007-07-21
I was messing around in synaptics, and I managed to uninstall the files needed for CPU frequency scaling. I have tried everything I can find in this forum, but no luck in getting it up and running again. It was working fine, until I messed it up. Now it runs on 100% all the time, and all the scaling software I install, says that my system does not support frequency scaling.

I have Ubuntu 7.04, and an AMD 64 3800+ X2, I'm running 32 bit Ubuntu.

How do I figure out what is missing?:confused:

---

### Post by msandoy on 2007-07-23
Bumping this message....

---

### Post by msandoy on 2007-07-26
Bumping this message again, and hoping for any sollution...

---

### Post by kevinlyfellow on 2007-07-26
Did you uninstall the applets?
```
 sudo apt-get install gnome-applets
```
You should then have a commandline program called cpufreq-selector.

You may need to change permissions on cpufreq-selector to get the cpu frequency monitor to adjust the frequencies.

If that tool isn't enough, you can install cpufrequtils
```
sudo apt-get install cpufrequtils
```

Edit: Sorry I reread your original post, this doesn't look like the answer

---

### Post by kevinlyfellow on 2007-07-26
If you go to file -> history in synaptic, you can see your activities on it.  Perhaps you could post your activities when you mucked up the cpu scaling?

---

