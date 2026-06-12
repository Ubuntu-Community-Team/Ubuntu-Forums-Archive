---
title: "Difficulty installing CUDA in Ubuntu 14.04.1 - GTX980"
date: 2015-02-06
forum: General Help
---

### Post by OpenFerret on 2015-02-06
Hi all,

I'm trying to install CUDA in ubuntu 14.04.1 (x86_64).  I have a GTX980 that I want to utilise as part of my university project.

I'm downloading the correct CUDA .run file from [here]("https://developer.nvidia.com/cuda-downloads-geforce-gtx9xx"), which installs an appropriate nvidia drivers as well as the CUDA software and testing files, but it requires me to stop X and execute the file from a virtual console / command line.  When ever I try to use Ctrl + Alt + F1 (or F2-6) I just get a black screen and no command line.  But I know one is there as I can still type commands to log on and reboot.  But without being able to see what I'm doing it makes installation difficult.  Has anyone else solved this issue or gone about installing CUDA + Nvidia drivers with a different way?

Many thanks in advance!

---

### Post by mcduck on 2015-02-06
botht nvidia drivers an cuda libraries & dev files are available through Ubuntu's repositories, so you might want to just use the package management instead of downloading & installing them manually.

---

### Post by OpenFerret on 2015-02-06
> **mcduck said:**
> botht nvidia drivers an cuda libraries & dev files are available through Ubuntu's repositories, so you might want to just use the package management instead of downloading & installing them manually.

Yes, but not the up-to-date versions.  Plus, the GTX9xx series require specific CUDA libs.  So I have to do it manually.

---

### Post by efflandt on 2015-02-06
Try it from booting in Recovery mode. From the resulting menu enable networking. If that pauses, wait until it returns to the menu, then go to root console and run or install anything you need to do from there. Since you are root in that case, you do not need to use sudo. When finished simply type **reboot** and hit Enter key.

---

