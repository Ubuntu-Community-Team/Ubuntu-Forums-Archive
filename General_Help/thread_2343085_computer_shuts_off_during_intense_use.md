---
title: "computer shuts off during intense use"
date: 2016-11-13
forum: General Help
---

### Post by jworr on 2016-11-13
I do scientific computing on my machine which is running xubuntu 16.04. I'll start up a job that pegs all 8 cores to 100% and let it run over night. The problem is in the last couple days my machine has been turning off in the middle of the night. It doesn't appear to be power outages as everything else in my house is fine. I'm not sure if my machine is overheating or if there is some critical bug. The problem started after I did an update about 3 days ago, though that could be a coincidence. How do I start to even determine if this is a hardware or a software problem?

thanks

---

### Post by ian-weisser on 2016-11-13
A critical bug in hardware would cause the system to hang or freeze, powered on.
Poweroff without warning is built into the hardware, usually to prevent heat damage.

Check your logs in /var/log/syslog and /var/log/syslog.1 for pre-poweroff warnings.
If there are no warnings in the logs, then it's certainly your hardware. Open it up, blow it out, check your fans, and consider other cooling strategies for high-heat periods..

---

### Post by jworr on 2016-11-16
I checked the logs as you suggested and there were no warnings. I opened up my case and apparently the dust filter in the front grew a sweater. Removing it solved my overheating problem. Thanks for the help!

---

### Post by mörgæs on 2016-11-16
Good, please mark the thread 'solved'.

---

