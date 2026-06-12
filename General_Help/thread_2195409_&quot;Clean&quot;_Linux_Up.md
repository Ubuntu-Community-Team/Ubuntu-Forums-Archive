---
title: "&quot;Clean&quot; Linux Up"
date: 2013-12-23
forum: General Help
---

### Post by blake4 on 2013-12-23
On Android, when RAM process is high, you can "Boost" it by cleaning the processes, etc. Can I do this on Ubuntu 13.10? With a Terminal command, maybe? To be exact, I'm using the most recent Kubuntu.

---

### Post by tfrue on 2013-12-24
I would assume that if you are using up a lot of your memory by having a lot of web browser tabs open, playing a game, or other resource hogs that closing out of them and making sure they're not running in the background would free or "Boost" the memory.

---

### Post by blake4 on 2013-12-24
Well, just "closing" doesn't usually work. I'm not a gamer, I usually have multiple Kate editors opened writing code for my site. Other than that, Chrome which has about 5 tabs open, two of which are YouTube or other streaming sites as well as a VirtualBox. It runs smoothly. It just glitches sometimes. What task manager would you recommend?

---

### Post by tfrue on 2013-12-24
The System Monitor package with Ubuntu works really good. If you want a command line process view, then you can use 'top', and use commands like 'kill appname' to end a process of the specified name.

---

### Post by electrohandyman501 on 2013-12-24
Sounds like you have quite a bit running. How much ram do you have and how much have you committed to your VirtualBox environment.

---

### Post by grahammechanical on 2013-12-24
The Software Centre has something called System Load Indicator that puts indicators in the top panel which show CPU and RAM usage as well as other things. To avoid swapping data into and out of the  swap partition Ubuntu will use cache memory. This can make it seem as if Ubuntu was using a lot of memory. What else is going to use RAM if the the OS? Actually I have seen a drop of 15 - 20% in RAM usage (1GB) from using 12.04 to 13.04 and on through to 13.10.

Mind you I would not use a virtual machine. I tried it and my system was not up to it. Needs lots of power in the CPU, RAM and Video adapter.

Regards.

---

### Post by tgalati4 on 2013-12-24
I like *htop* to monitor what I have running.

Open a terminal:

```
sudo apt-get install htop
htop
```

Control-C to quit.

You can kill processes from there.

---

