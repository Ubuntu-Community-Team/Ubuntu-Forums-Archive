---
title: "I can't get to the Ubuntu Desktop"
date: 2024-07-07
forum: General Help
---

### Post by jjmgr2353 on 2024-07-07
Greetings from Valencia, Spain.

Even though I am not a newbie I have just used Ubuntu for general purpuses tasks. However, sometimes I erase things that I should not and I get in trouble. I use an relatively old PC with a dual boot Ubuntu 24.04 LTS /Windows 10 (I cannot upgrade to Win 11). I only use Windows when working with large reports, worksheets, AutoCAD and Photoshop. But most of my time is spent on Ubuntu. Two days ago I tried to install Fuse via a repository (*sudo add-apt-repository ppa:appimagelauncher-team/stable* 
) which throw me an error in the command line. I just delete the repository from the update app in Ubuntu Apps (I received a warning which I ignored). When later I tried to start my session in Ubuntu, I pass the boot load phase, I choose Ubuntu, then it did not start, I got to a black screen and ubuntu started to run some checks, by the time it reached "Started cups.service - CUPS Scheduler" which is checked in green as OK (see image attached), the cursor blinks forever and I have to reboot. Fortunately for me, I can boot to Windows but no to Ubuntu anymore.
Sorry for so long and wordy text.
 Can some one give a hand on this, so I can log into Ubuntu again - I have a ton of info (without backup - my fault) in there.
Thanks a lot.[IMG]https://ubuntuforums.org/asset.php?fid=287028&uid=2176311&d=1720377057[/IMG]

---

### Post by yancek on 2024-07-07
>  Two days ago I tried to install Fuse via a repository (*sudo add-apt-repository ppa:appimagelauncher-team/stable*

Why?  You could install it from the package manager or a terminal with the apt command.  Does the ppa have a newer version?   Did you run apt update and apt upgrade first?  Not knowing what warning or error you got I don't see how anyone can help.  Do you have a 'live' Ubuntu usb (or any LInux)?  If so, you should be able to boot it and access and copy your data to another drive.  I don't use appimagelauncer but maybe someone else familiar with it will see your thread.

---

### Post by tea for one on 2024-07-07
> **yancek said:**
>  Do you have a 'live' Ubuntu usb (or any LInux)?  If so, you should be able to boot it and access and copy your data to another drive.
Yes, perfect advice - this is your priority task to solve "[COLOR="#FF0000"]I have a ton of info (without backup - my fault) [/COLOR]"

---

### Post by jjmgr2353 on 2024-07-09
Thanks for your reply. The problem is that I've been asked a machine and user names which I don't remember. How can I find out them when I enter using root in Recovery Mode?

---

### Post by jjmgr2353 on 2024-07-09
[COLOR=#000000]Thanks for your reply. The problem is that I've been asked a machine and user names which I don't remember. How can I find out them when I enter using root in Recovery Mode?[/COLOR]

---

### Post by ActionParsnip on 2024-07-09
```

ls /home

```
should do it

---

