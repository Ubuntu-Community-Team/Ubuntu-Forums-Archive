---
title: "Should I reinstall?"
date: 2008-02-27
forum: General Help
---

### Post by BetterSense on 2008-02-27
I know it's legacy logic, but I don't know what else to do. I'm still having the same lockout problem I have been..I cannot open synaptic except from the command line, I cannot go into 'administrator mode' to enable restricted drivers, and I can't even set my clock (which actually needs set). I always prompts me for my password and then nothing happens. I was just going to reinstall KDE but I logged into my wife's account with gnome and had the same issues. 

When I do reinstall, could I leave my /home, which is part of a lvm, and just reinstall to the partition I made for the OS, or could this problem follow me because of files that might be stored in /home?

---

### Post by stooshbunutu on 2008-02-27
Not sure whether you should re-install or not but as regards to the /home directory:

Unless you command-line installed a program to the /home directory then no OS files will be installed on a seperate partition to the /home directory.

I'm not too sure about the Kubuntu release but the alternate CD has two options you could try:
1. Rescue a broken system, this may help
2 Install in text mode, and then the partitioner wizard will allow you to select to only reinstall over one partition as one of the various options

Hope this helps

---

### Post by BetterSense on 2008-02-27
Ok something seriously strange is going on here. I installed ubuntu (using the alternate text-mode disk) onto an old laptop to keep at work (then apt-get install kubuntu-desktop). I'm having the EXACT SAME issue with that completely different computer that I just installed on about 3 days ago. I can't enter administrator mode or set my clock. Why does linux hate me?

Correction: I can open synaptic on the laptop at work, unlike at home. But I still can't enter administrator mode to enable restricted drivers or even set my clock.

---

