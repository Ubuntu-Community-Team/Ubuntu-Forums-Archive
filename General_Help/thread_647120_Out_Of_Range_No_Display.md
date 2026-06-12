---
title: "Out Of Range: No Display???"
date: 2007-12-22
forum: General Help
---

### Post by TheManzine on 2007-12-22
Hi Um I am having an issue with my linux that installed just about a day ago. I was changing some settings in nvidia-settings and now when I log into ubuntu it says on my monitor "out of range" and will not display even though I can hear the OS loading. The only other thing I can think that I might have changed was under "screens and graphics" i think and I might have made my monitor "plug-n-play" but that might have already been turned on and working fine. I have no idea where to start and since I just installed linux about a night ago I wouldn't like to reinstall. I am now on my vista and I reinstalled the Nvidia driver which was missing from my windows after installing Linux and then tried reloading Linux again but it still ahs the same error. So I have no idea how to access the nvidia-settings in Linux because I can't see what the hell I'm doing. Is there anyway to recover my linux display through vista?
Confused..

---

### Post by Nano Geek on 2007-12-22
Try this.

Boot into Ubuntu recovery mode, and type this into the terminal.```
dpkg-reconfigure -phigh xserver-xorg
```Answer the questions, reboot, and Ubuntu should work again.

---

### Post by TheManzine on 2007-12-22
Awesome, thanks for the tip, Worked like a charm.

---

### Post by Nano Geek on 2007-12-22
Glad it worked. 

Merry Christmas!

---

