---
title: "Launcher missing after installing nVidia driver"
date: 2012-11-24
forum: General Help
---

### Post by epqrs on 2012-11-24
I did a fresh install of Ubuntu 12.10 and installed nVidia driver  'current'. But on restart, the launcher icons went missing. The screen size reduced  to 1024x768. I am able to right click on the blank desktop and create a folder and an  empty document, but how do I launch applications to fix this ?

---

### Post by stinkeye on 2012-11-24
It's some sort of bug to do with linux-headers.
Ctrl+alt+t to open a terminal and run each command....
```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```
Restart.

---

### Post by NikTh on 2012-11-24
Hi , 
if above not working , try the same sequence with nvidia-experimental 
Thanks

---

### Post by IanVaughan on 2012-12-15
This solved it for me, I have a 9200GT, and after upgrading I only saw 1 of my two monitors, on login, either via guest or my account, and then once logged in saw no launcher/menu bar.

Dropping into a shell and doing this worked a treat, many many thanks @stinkeye

> **stinkeye said:**
> It's some sort of bug to do with linux-headers.
Ctrl+alt+t to open a terminal and run each command....
```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```
Restart.

---

### Post by shobe on 2013-02-01
It worked perfectly for me with just the first two commands. I also tried the third one, but it had no effect.

---

