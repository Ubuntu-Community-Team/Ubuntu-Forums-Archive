---
title: "Kernel Panic - Something to do with disk check?"
date: 2007-07-17
forum: General Help
---

### Post by Sushisource on 2007-07-17
Hello,

I decided to turn here for some help, since the bug I posted [here ]("https://bugs.launchpad.net/ubuntu/+bug/126227")doesn't seem to be drawing any attention.

Using kernel 2.6.20-16-generic my Kernel consistently panics while booting, just after trying to check /dev/sda1

Unfortunately you can't see everything in this shot, but here is what my screen looks like after the disk check is interrupted:
[http://img516.imageshack.us/img516/7258/cimg0961se2.jpg](http://img516.imageshack.us/img516/7258/cimg0961se2.jpg)

I had a problem with my kernel panicking before, and I fixed it with [these ]("http://ubuntuforums.org/showthread.php?t=299101")steps, but that doesn't work anymore.

Any help is appreciated, thanks!

---

### Post by Koybe on 2007-07-17
When you start your computer, grub should ask you some different kernel to boot. Does this happen with each kernel?

It seems that your root (/) partition is not correctly mounted.

---

### Post by Sushisource on 2007-07-19
This happens with the recovery kernel as well. How should I go about remounting my root?

New info: It seems about 1 in every 5 reboots or so it randomly works, only to fail again the next time it's shut down.

---

### Post by Sushisource on 2007-07-19
I hate to be rude, but I'm going to bump this because I still can't solve this problem.

---

