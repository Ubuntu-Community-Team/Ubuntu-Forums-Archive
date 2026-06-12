---
title: "Ubuntu Software Center Crashing 12.10"
date: 2012-12-09
forum: General Help
---

### Post by archmagus501 on 2012-12-09
Ubuntu Software Center crashes every time I try to launch it. I get no warning of anything going wrong, I simply get the spinning beach ball and the window darkens after a few seconds. When I go to close it, I get an option to wait or force quit. Upon selecting wait, nothing happens and upon selecting "force quit", the window closes, but the process still remains in the system monitor.

Upon searching the internet, I find workarounds for 12.04 and older which deal with modifying a specific line of code in a file. The line which I am supposed to modify is missing when I try to follow the workaround. Even though the workarounds say they're for older versions, I try them but nothing has worked.

I have tried adding in the fixed line, adding in the broken line, closing everything and then trying to fix it, and going through synaptic package manager and re-installing USC, doing a complete removal and then installing it again, and USC still crashes when I try to launch it.

I have attached a screenshot of what happens when I try to launch USC

---

### Post by mörgæs on 2012-12-09
Hi, welcome to the fora.

What happens if you close all windows and run the commands

```
sudo apt-get update
sudo apt-get upgrade
```?

Please post all error messages which might appear.

---

### Post by archmagus501 on 2012-12-09
No errors after running either one

---

### Post by mörgæs on 2012-12-11
Can you install using 

```
sudo apt-get install <some-package>
```

?

By the way, this is worth reading:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by archmagus501 on 2012-12-11
I installed Spotify for Linux using Terminal before I upgraded to 12.10, and have not installed anything since. Synaptic Package Manager is working, and I used it to try and re-install USC, and then tried completely removing USC and then installing it again, but that didn't resolve the issue.

I am relatively new to Ubuntu. I installed Ubuntu 12.04 using a live CD over the summer, and then upgraded to 12.10 when it came out.

---

### Post by mörgæs on 2012-12-12
I can't give an exact solution, as I never use Software Centre myself. 

If you tell exactly the steps you have tried (and in general follow the advice in the link I posted) there is a chance that someone else is able to help.

---

