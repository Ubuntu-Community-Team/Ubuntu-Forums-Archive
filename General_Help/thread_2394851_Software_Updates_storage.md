---
title: "Software Updates storage"
date: 2018-06-22
forum: General Help
---

### Post by ramanterola on 2018-06-22
Greetings Ubuntu virtuoso(s):

I have an interesting question.  I am running Lubuntu in a Dell toy.   I call it a toy because it is all plastic, with a celeron chip and 32 Gb of Emmc.   So here is my question this morning:  When the OS downloads updates, do these updates stay in the computer thus consuming valuable harddisk space?  Do I need to do anything manually or create a script to do housekeeping, or are they pushed into the OS and cleaned afterwards automatically?    

TY

R

---

### Post by plucky on 2018-06-22
> **ramanterola said:**
> Greetings Ubuntu virtuoso(s):

I have an interesting question.  I am running Lubuntu in a Dell toy.   I call it a toy because it is all plastic, with a celeron chip and 32 Gb of Emmc.   So here is my question this morning:  When the OS downloads updates, do these updates stay in the computer thus consuming valuable harddisk space?  Do I need to do anything manually or create a script to do housekeeping, or are they pushed into the OS and cleaned afterwards automatically?    

TY

R

The .deb files are stored in ```
/var/cache/apt/archives
```.
The command ```
sudo apt clean
``` will delete them.

Good Luck

---

### Post by oldfred on 2018-06-22
Log files also grow, you may want to houseclean those out if no issues.

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

