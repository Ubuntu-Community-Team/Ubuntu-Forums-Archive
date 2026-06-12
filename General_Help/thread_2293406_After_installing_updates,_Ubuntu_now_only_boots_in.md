---
title: "After installing updates, Ubuntu now only boots into grub command line"
date: 2015-09-04
forum: General Help
---

### Post by brandon36 on 2015-09-04
I have been running a dual boot setup with Ubuntu 15.04 and Windows 10 for about a week now and earlier today Ubuntu asked if I wanted to update some packages. I chose yes, and did some surfing while those were going in the background. My laptop suddenly restarted, and now instantly boots into grub command line. I'm guessing all of my files are fine, but simply a boot file or path might be messed up. Does anyone have any suggestions on how I can go about fixing this issue? Any help or advice would be greatly appreciated!

---

### Post by s0c0 on 2015-09-05
There is something viscous that came down in an update recently, I first noted it here: [http://ubuntuforums.org/showthread.php?t=2293373](http://ubuntuforums.org/showthread.php?t=2293373) and this bug robbed me of 4 hours of development at work today trying to fix my system. And now its robbing me from working on my personal projects at home ](*,)This just happened to me again after trying to install a new package through apt-get I was told to run a dpkconfigure -a command or something and then it occured again. I am about to fix this damn issue for the second time today. I'll post full steps in there and then hopefully put together a bug report for Ubuntu on this matter. This is annoying. I'm never venturing outside of the LTS releases again.

---

