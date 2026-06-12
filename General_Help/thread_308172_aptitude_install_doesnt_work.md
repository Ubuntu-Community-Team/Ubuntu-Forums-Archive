---
title: "aptitude install doesnt work"
date: 2006-11-27
forum: General Help
---

### Post by P4R on 2006-11-27
Well, I got Ubuntu 6.10 about 4 weeks ago as an experiment, I found out that I really liked it, and decided to fully format the harddrive and install ubuntu.

Before the re-installation, I had lots of things installed (Flash 9, JRE, etc). But After I re-installed ubuntu, sudo aptitiude install name_here does not work! For example, I type sudo aptitude install wine and it goes through the whole process, but when I try to open something .exe, it says I cant open it, so I right click it hoping to see "Open with Wine', but it isnt on the list! This happens with everything i try to install from the terminal. Even flash 9 plugin beta 2 doesnt work. What happened?

And, yes, I do have ALL repositories enabled in sources.list, I am logged in as root (since I am the only user), and I have not edited anything that has to do with how the terminal runs.


I tried rebooting the pc, but still, none of the stuff I tried to install shows up.

So, can you help me?

---

### Post by dcstar on 2006-11-27
> **P4R said:**
> Well, I got Ubuntu 6.10 about 4 weeks ago as an experiment, I found out that I really liked it, and decided to fully format the harddrive and install ubuntu.

Before the re-installation, I had lots of things installed (Flash 9, JRE, etc). But After I re-installed ubuntu, sudo aptitiude install name_here does not work! For example, I type sudo aptitude install wine and it goes through the whole process, but when I try to open something .exe, it says I cant open it, so I right click it hoping to see "Open with Wine', but it isnt on the list! This happens with everything i try to install from the terminal. Even flash 9 plugin beta 2 doesnt work. What happened?


Firstly, use Synaptic for package management, it provides a far friendlier interface for installing packages.

Secondly, if you have indeed installed wine, you may need to run winecfg from a user terminal session (NOT root).

---

