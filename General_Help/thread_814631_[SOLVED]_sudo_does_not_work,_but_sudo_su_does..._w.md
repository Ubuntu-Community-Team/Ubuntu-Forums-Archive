---
title: "[SOLVED] sudo does not work, but sudo su does... why?"
date: 2008-05-31
forum: General Help
---

### Post by unutbu on 2008-05-31
I recently bumped into a command which returns "Permission denied" when I run it with sudo. But I found that if I run it after doing `sudo su`, it actually works! What do you suppose is going on?

```
out@themovies:~% sudo echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```
But this does work!
```

out@themovies:~% sudo su
root@themovies:/home/out# echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

So you can feel safe trying this yourself, the commands come from here:

[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

To see what scaling governors are available:

```
out@themovies:~% cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative powersave userspace ondemand performance 
```

To see what scaling governor you are currently using:

```
out@themovies:~% cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
```

To reset your scaling governor:

```
out@themovies:~% sudo su
root@themovies:/home/out# echo GOVERNOR > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
where GOVERNOR is whatever governor you were previously using.

---

### Post by quelx on 2008-05-31
[http://ubuntuforums.org/showthread.php?t=412329](http://ubuntuforums.org/showthread.php?t=412329)

---

