---
title: "Google talk plugin"
date: 2012-12-07
forum: General Help
---

### Post by Torack on 2012-12-07
So I installed the google talk plugin about a month or two ago. 

Last week I noticed that the updates program wouldn't open. I tried updating from the terminal. Same thing happened.

The error message I got from both the update application and the terminal: "E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened. "

Ubuntu software center crashes before it even opens, as well. And I do think they are related, though I might be wrong.

---

### Post by mörgæs on 2012-12-08
Hi, welcome to the fora.

Please boot the comuter and close all windows which might open. After that run

```

sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

```

---

