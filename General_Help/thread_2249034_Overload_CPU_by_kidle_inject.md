---
title: "Overload CPU by kidle_inject"
date: 2014-10-19
forum: General Help
---

### Post by tarzq306 on 2014-10-19
hello anybody, can you help me to figure out what the problems that make my ubuntu 14.04 LTS running very slow and consume about 50% my CPU. i've never seen problem like this before using ubuntu 12.04. After using ubuntu 14.04 for 2-5 hours my cpu drastically increase it load, first i check in system monitor to make sure which process using more resources, but it seems there's no process which take a lot of CPU resources, then i move to terminal and runing TOP command then i'm see there's process called kidle_inject with 4 threads from 0 to 3. I'm try to google everywhere but there's no answer to provide how to solve this problem. OK, previously i have install thermald on my ubuntu and activating intel p-state but after i read some thread that suggest to disable intel p-state and give 10 value to swappiness then i'm change my ubuntu configuration then restart my computer. After all, i think it was works for me but like i say after running for more than 2 hours even less than 1 hour my CPU load become overload again, and i try to check with TOP it always show the same result that kidle_inject always take more resources of my CPU, for now there's no way than take reboot my computer when thoose problem coming. Please give me some help

---

### Post by Doug S on 2014-10-19
Have you seen [this]("http://askubuntu.com/questions/482307/kidle-inject-uses-cpu-power-without-apparent-reason")? Apparently kidle_inject is forcing 50% idle into threads.

 I run the intel_pstate driver on my 14.04 test server, but I do have any kidle_inject thing.

Edit (I am guessing a little here): I think that kidle_inject is part of thermald and not as a result of intel_pstate only. I also think your processor is getting hot, causing thermald to kick in this stuff. Try uninstalling thermald, but monitor your CPU temperatures.

As for the intel_pstate driver, there were issues a year ago and the recommendation was to disable it. It is now enabled by default in 14.10.

Edit 2: See [also]("https://www.kernel.org/doc/Documentation/thermal/intel_powerclamp.txt").

---

### Post by tarzq306 on 2014-10-19
OK,thanks for help as soon my problem solve i'll mark this thread as solve, soon

---

### Post by Doug S on 2014-10-19
> **tarzq306 said:**
> OK,thanks for help as soon my problem solve i'll mark this thread as solve, soonI would be very interested in your findings, particularly if your CPUs run hot or not without thermald.

---

### Post by tarzq306 on 2014-10-19
thanks Doug S for your tip, i should running my ubuntu for few hours to make sure everything works fine, then i'll mark this thread as SOLVED, for now it seem work fine

---

### Post by tarzq306 on 2014-10-19
> **tarzq306 said:**
> thanks Doug S for your tip, i should running my ubuntu for few hours to make sure everything works fine, then i'll mark this thread as SOLVED, for now it seem work fine

thanks a lot dude, it seems my problem fix now. now  time to mark these  thread as solved.hope this troubleshoot could help anyone who getting  same issue.Again, thanks a lot

---

