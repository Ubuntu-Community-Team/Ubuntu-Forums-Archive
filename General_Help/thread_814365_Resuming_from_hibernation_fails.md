---
title: "Resuming from hibernation fails"
date: 2008-05-31
forum: General Help
---

### Post by Lr5 on 2008-05-31
After upgrading to the latest kernel in Ubuntu 8.04 hibernation works, but resuming from it doesn't. All I have found about it this far are some lines in /var/log/syslog:

```
May 31 13:06:06 lr5-desktop2 kernel: [   38.774956] Attempting manual resume
May 31 13:06:06 lr5-desktop2 kernel: [   38.774959] swsusp: Resume From Partition 8:6
May 31 13:06:06 lr5-desktop2 kernel: [   38.774960] PM: Checking swsusp image.
May 31 13:06:06 lr5-desktop2 kernel: [   38.775085] PM: Resume from disk failed.
```

I have tried using the hibernate button and "sudo hibernate --force" (--force due to nvidia-glx-new), but neither helps when trying to resume.

Anyone knows how to solve this problem? Hibernation and resuming worked fine with the last kernel, but I'd prefer to use the latest one.

---

### Post by Shne on 2008-06-01
Well, I can say I have the same problem.
Hibernation worked fine with 2.6.24-16 but doesn't now in 2.6.24-17
With the newest kernel, the Ubuntu loading screen freezes while the orange bar is going back and forth, and then nothing appears to be happening until I reset the comp and it starts normally.

I can also find those lines in /var/log/syslog you found, but I don't know if they only appear when it's not working.

Going into hibernation appears to be working as before.

edit: it seems the good people in this thread: [http://ubuntuforums.org/showthread.php?t=812095](http://ubuntuforums.org/showthread.php?t=812095) are havin the same problem. the only solution so far is to use the 2.24-16 kernel.
A bug report has also been filed: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272)

---

### Post by Lr5 on 2008-06-01
After examining it a bit further, I noticed that the hibernation itself resumes, but X server fails to do that. If I do ctrl+alt+f1, I can get to the shell login, but if I try to go back to X, it freezes and doesn't let me change back with ctrl+alt+f1.

---

### Post by DeVonne on 2008-06-01
How about ctrl + alt + F7
try that and let me know I am curious

---

### Post by brigadoon on 2008-06-01
The apmd (Advanced Power Management (APM) daemon) command may help. In a command line type man apmd to learn more. One of the options is resume. Good luck.

---

### Post by Lr5 on 2008-06-01
> **DeVonne said:**
> How about ctrl + alt + F7
try that and let me know I am curious

That freezes the system and doesn't let me change back to others.

---

### Post by Lr5 on 2008-06-17
Kernels -17 and -18 didn't work so I just went back to the -16 kernel. Now the -19 kernel (2.6.24-10-generic) works too. Posting here in case someone finds this thread when looking for help.

---

