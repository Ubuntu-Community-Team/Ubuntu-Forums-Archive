---
title: "Ubuntu 14.04 freezing"
date: 2014-08-22
forum: General Help
---

### Post by raffaele5 on 2014-08-22
I've recently installed ubuntu 14.04 on my Dell XPS and I am experiencing a strange freeze issue.



Everything  works perfectly for a couple of days (of being continuously logged in  with my account)  then suddenly, while i am using the computer, Ubuntu  freezes for several minutes every time i try to open or close a new  windows (browser, calculator, terminal, etc..)

After a few minutes the freeze is over and everything works fine until i try to open or close another window.


Logging  off (usually by using a strong kill -9 -1) fixes the problem, no need  to reboot, but after another couple of days the issue comes back.

Any idea on what it is and how to fix it?


Raf


P.S.

I  checked dmesg and saw nothing there, I also checked the memory and CPU  while ubuntu on my computer freezes by ssh in from another location  (which I can do just fine) and everything seems OK.

---

### Post by mikewhatever on 2014-08-23
Could be some xserver problem. Logging off restarts it, making the freezes go away.
Check /var/log/Xorg.0.log for clues. It might also be usefull to know the graphics specs.

---

