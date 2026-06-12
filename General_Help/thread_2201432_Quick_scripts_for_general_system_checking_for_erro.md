---
title: "Quick scripts for general system checking for errors"
date: 2014-01-24
forum: General Help
---

### Post by startas on 2014-01-24
So, i never thought about it, but now i'm wondering if there is any kind of prepared scripts to launch in terminal for checking all the log files and anything else for errors, warnings, maybe some other bad stuff in kernel / booting / drivers / something else. Maybe there already is a thread with an answer and i didn't notice it ?

---

### Post by tgalati4 on 2014-01-24
I don't know of a comprehensive script for checking, but there are several tools for simple searching through log files.  If you have a graphics problem look through:

```
grep EE /var/log/Xorg.0.log
```

For just warnings:

```
grep WW /var/log/Xorg.0.log
```

Each log file has its own key words to search, so it is helpful to read through some of the log files so you can see what these warnings look like.  Because there are so many log files and there is no standard format, the warning messages are all different and require different search terms.

---

### Post by startas on 2014-01-24
Yes, i know, thats why i asked if there already exist some bigger group of commands, which would check the system for general errors/warnings.

---

### Post by ian-weisser on 2014-01-24
Prepared scripts? No.
If developers know about an error, they will usually fix the error, or find a way to recover from the error rather than writing a (unhelpful) find-the-error-in-a-log tool.

Sometimes the easiest way is to use grep.
```
grep --ignore-case err /var/log/dmesg
```

---

### Post by startas on 2014-01-24
But usually users report errors, and if users dont know what errors they have, they cant help devs, plus errors can exist not only because of bugs in code. I.e., I find linux to be very uncomfortable os because there is always something wrong, i.e. file browsers are slow, the whole gui (doesnt matter which de) is somewhat slow and lacking smoothness, boot process is very long, especially in ubuntu with all its mixed boot things like systemd/upstart/......, and millions of other things, but there is no easy way to check what is wrong (if there is any bad things), and if devs would know, what they are doing, there wouldnt be such things as bug reports and so on, not to mention, that linux in general is community supported os and it only lives because of that.

"linux" - all linux distributions.

---

### Post by tgalati4 on 2014-01-24
Your system will run with warnings, but errors will cause major loss of functionality, so searching for them on a general basis on a working system is rather pointless.  So you would normally not need to search for errors, because your system is either running correctly or not.  If it is not, then you would normally describe what is not working and the devs or forum members trying to help will first ask you to look through specific log files.

The "million" things that you describe is rather vague.  I don't have those issues, so perhaps your hardware is not strong enough to run a modern distro.  I don't care about booting time, because I only reboot once every 3 months, I only put my machine to sleep and it comes back in 3 to 8 seconds.  The graphics are snappy because I'm running a low-overhead desktop environment.  

So, describe the specific problems you are having and perhaps we can help.

---

### Post by ian-weisser on 2014-01-24
"Something wrong" may not be a loggable error or warning. Or it may be a well known issue already not worth warning about.

Example: A slow GUI environment may be due to too many processes running, or a video hardware manufacturer's awful linux support, or a couple settings in Xorg.conf, or the system simply may not meet the minimum recommended capabilities. Some of those may cause log entries, some may not. 

I think about it like an automobile: It's unreasonable to expect an auto manufacturer to warn you of every possible event. You won't see "Warning: The car is slowing down because you are driving uphill and need to apply the accelerator...if it's lawful, and if nobody is in front of you, and if your view is not obstructed, and if you can reach the pedals." New drivers must learn skills. New OS users must also learn new skills.

---

