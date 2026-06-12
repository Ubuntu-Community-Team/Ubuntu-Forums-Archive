---
title: "[SOLVED] High CPU usage for no reason"
date: 2008-01-09
forum: General Help
---

### Post by jdfoote on 2008-01-09
I am very new to Linux, and have had Ubuntu on my computer for just a few months.

I have noticed that it sometimes runs slow, but thought that it was just having a somewhat dated computer. 

However, I just noticed that the Resources tab of system-monitor shows that I am generally up between 70-100% cpu usage, even with no major apps running. When I look at processes, though, the total usage is only 20-25%.

Has anyone had a similar problem?

I'm running Gutsy on an emachines box and the 2.6.22-14-generic kernel.

---

### Post by kdwillia on 2008-01-09
If you go to the terminal and run "top", you can see all the processes in real time and the amount of CPU cycles they are taking up.

---

### Post by jdfoote on 2008-01-09
Ah yes - I am an idiot. It was the Boinc client, which I forgot that I had installed.

Great tip - thanks so much!

---

