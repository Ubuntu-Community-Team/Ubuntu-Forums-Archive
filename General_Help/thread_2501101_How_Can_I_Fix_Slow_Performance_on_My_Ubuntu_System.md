---
title: "How Can I Fix Slow Performance on My Ubuntu System After Recent Update?"
date: 2024-09-23
forum: General Help
---

### Post by deftsoft on 2024-09-23
Hi everyone,


After a recent update to my Ubuntu system (currently running Ubuntu 24.04.1), I’ve been experiencing significant slowdowns, particularly when opening apps or switching between windows. I haven’t changed any hardware or installed any new programs, so I’m not sure what’s causing this issue.

Here’s what I’ve tried so far:

[LIST]
[*]Checked CPU and memory usage with top and htop (everything seems normal).
[*]Cleared out old caches and temporary files.
[*]Disabled unnecessary startup applications.
[*]Ran sudo apt-get update && sudo apt-get upgrade to ensure everything is up-to-date.
[/LIST]

Despite these efforts, the performance issues persist. Has anyone else experienced this after an update, or can you suggest any other troubleshooting steps I might have missed? I’d appreciate any advice!


Thanks in advance!

---

### Post by TheFu on 2024-09-23
Look at the log files.

---

### Post by ActionParsnip on 2024-09-24
If you make a fresh Ubuntu user and log in as that, is the system slow there as well?

---

### Post by TheFu on 2024-09-24
> **ActionParsnip said:**
> If you make a fresh Ubuntu user and log in as that, is the system slow there as well?

This will help determine if it is a system-wide issue or just your username's specific settings causing the performance problem.  If there's nothing in the logs, this will be helpful.

The most common issues for performance changes are network issues (lots of things in Linux use networking to check stuff, even sudo uses network system calls to check that the current hostname is) or DNS. Slow DNS can really impact a system.  There are tools that can be used to find the fastest DNS for you location.  Often, that isn't the one your ISP provides.   

Hardware that is just beginning to fail will take time to do things.  I had a HDD that started failing last spring. There were HDD resets happening about 2x a second and the entire system was slower due to the retries and resets.  And a failing, but still working, 

PSU can cause performance issues too. Usually, until the PSU fails completely, the problems from it can only be seen in other components.  Had a PSU fry a GPU some years ago.  Eventually, replaced the GPU only to find the factory new one was throwing errors in the logs too, but still sorta worked.  Replaced the PSU and the new GPU was fine - the older GPU was dead and didn't work at all with the PSU.

Lots of people only get high-cost PSUs. Not me. I use whatever came with the case until there's a problem (often 10 yrs later). Around 2010, I saw a deal on some Seasonic Bronze PSUs, so I bought 3 to have around ($45/ea).  Seasonic, at the time, was very reputable and known for quality while being quieter than most others.  All three of my desktop systems have those Seasonic PSUs inside and have for years.

Anyway, my point is that the system logs can help nail down issues.  Just look for errors and warnings in those.  Fix the first that you see. Often the first one will correct all the others.  If not, keep working your way down the timeline for other errors and warnings.

---

