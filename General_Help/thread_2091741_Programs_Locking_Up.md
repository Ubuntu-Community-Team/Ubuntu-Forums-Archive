---
title: "Programs Locking Up"
date: 2012-12-05
forum: General Help
---

### Post by TheMoatMonster on 2012-12-05
Hello! I'm a long-time PC user, and I've been using Windows for years.  But I recently decided to try out Ubuntu, and installed it on a partition  of my Windows drive, using the auto-installer provided on the Ubuntu  website.

However, I am running into some very frustrating  problems. When running a single program, everything is fine, but when  trying to use multiple programs at once, they all start locking up.

I  tried watching the System Monitor when the lock-ups started, and I  didn't see any increase in memory or swap usage (Memory usage usually  hovers around 700 MB).

I've tried re-installing Ubuntu a number  of times, both on new partitions and on separate drives, but the problem  persists. I think it might be hardware/driver related, but I'm not 100%  sure.

I should mention, in case it isn't clear, that I'm a  complete Ubuntu newbie. I'm very proficient with Windows, but Ubuntu is a  whole different beast. Please be patient with me.

In case it helps at all, here are my system specs:

Graphics card: ATI Radeon HD 3850 (Using proprietary drivers)
Processor: AMD Phenom 9650 Quad-Core
Memory: 3 GB

Ubuntu version: 12.04 LTS (64 bit)

I'm eagerly awaiting any suggestions you might have. Thank you very much for your time.

---

### Post by Kirk Schnable on 2012-12-08
First we need to find out why things are locking up. This could be due to memory usage, CPU usage, disk usage, or possibly other factors as well. 

You should be able to use output from top as a good starting point to understanding what's going on. If you don't know how to read the information, screenshots might be useful to us, or running top in batch mode to produce text output for us. 

[http://linux.die.net/man/1/top](http://linux.die.net/man/1/top)

Top shows CPU usage, memory usage, and other useful information by process. It's a bit more detailed than most graphical system monitors.

---

