---
title: "apt-get"
date: 2007-10-21
forum: General Help
---

### Post by skm376 on 2007-10-21
I'm running Ubuntu server edition 7.10 on a new machine I just got.  I am trying to configure the machine remotely, but everytime I try to use apt-get it prompts me to insert the install cd.  I can't do this because I am not physically at the machine.  How can I force apt-get to download and install packages from repositories instead of the cd.  My network connection is up and running.  I am trying to install gcc.

---

### Post by DagMan on 2007-10-21
sudo nano /etc/apt/sources.list
and comment out or remove the entry that refers to the cd, then
sudo apt-get update

to get gcc and friends
sudo apt-get install build-essential

---

