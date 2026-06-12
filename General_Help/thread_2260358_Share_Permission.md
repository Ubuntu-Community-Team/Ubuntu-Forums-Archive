---
title: "Share Permission"
date: 2015-01-11
forum: General Help
---

### Post by paul189 on 2015-01-11
Hi,

This is my first post after switching to Ubuntu 14.04 LTS, desktop version, for my media server.

I am having problems creating share on an extra drive.

I can create and access shares on the system drive. But I have added a 2nd drive to hold my data (will probably RAID in the near future) however when I create a share using the GUI on this drive it is inaccessible. Can anyone shed any light on what i am doing wrong?

Here are the share setting for the working share
[ATTACH=CONFIG]259164[/ATTACH][ATTACH=CONFIG]259165[/ATTACH]

Here are the settings for the share that fails
[ATTACH=CONFIG]259166[/ATTACH][ATTACH=CONFIG]259167[/ATTACH]

---

### Post by paul189 on 2015-01-16
I discovered the problem. 
I had to give 'other' execute permission on all folders from the root to the shared directory. 


I.e the share was located at /media/pau/data/share, I had to give 'other' execute permisson on /media, /media/paul, /media/paul/data

---

