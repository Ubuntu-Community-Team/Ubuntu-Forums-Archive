---
title: "Can’t open anything after updates"
date: 2021-01-08
forum: General Help
---

### Post by relentlessnotions on 2021-01-08
[]("https://askubuntu.com/posts/1306018/timeline")  
          
                                            I installed wine then installed updates through Software Updater. I  was then promoted to restart which I did. However, upon restarting, no  applications or files are able to be opened, including the terminal. The  application/file that is opened just hangs and the window becomes  unresponsive although I am able to move the mouse around.


 Everything works fine if I boot in recovery mode. Please help

---

### Post by Impavidus on 2021-01-08
Have you tried an older kernel? The grub menu must list them next to recovery mode. There may be a problem with your kernel.

3 days ago I got a new kernel with my regular upgrades, [s]5.4.0-58[/s] 5.4.0-59. I just got [s]5.4.0-59[/s] 5.4.0-60. That's pretty fast.

---

### Post by relentlessnotions on 2021-01-08
Just tried that. Thanks, it's definitely the updated kernel. So the problem is caused by 5.8 and everything works fine on 5.4. Is there any fix for this besides having to boot using the older kernel each time?

---

### Post by ActionParsnip on 2021-01-08
Did you post this on Launchpad.net too....? Sounds familiar

---

