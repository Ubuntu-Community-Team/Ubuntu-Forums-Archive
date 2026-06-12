---
title: "constant iowait cpu usage"
date: 2005-10-24
forum: General Help
---

### Post by Monkey_See on 2005-10-24
Hello,

I recently setup Ubuntu 5.10 on a new laptop, and everything seems to work very well... except the system monitor panel applet always shows the cpu shows iowait processes taking up about 45%-55% of cpu resources.  "top" only shows few percent being used up by various system processes during idle.

This (I think) makes it so the cpu can not scale down fully when unplugged and idle  , and also it makes it so the cpu can not be scaled up fully when under load because only ~50% is available for user resources.  Not such a pain when it is plugged in, but causes somewhat shortened battery life and I don't think I am getting the full benefit of my nice new athlon 64 4000+ (although the system still feels somewhat snappy).

I'm not exactly sure where to start looking to fix this, as I'm not exactly sure how the system makes use of iowait cpu cycles.

So does anyone have any insight into how to correct this?  Or where I could start to look?

Thanks
Monkey_See

---

### Post by JediCowboy on 2005-11-01
Did you ever find a solution to this?  I'm having the exact same issues and can't seem to find what I need on Google.

---

### Post by Monkey_See on 2005-11-13
Unfortuantly I have not found a solution to this problem on my machine, however I have linked this behaviour to the "double clock" problem and many of the posted solutions do not work properly for me.  I have read that the new kernels (2.6.14.2 stable) help solve this... though I have yet to test this.

[http://www.ubuntuforums.org/search.php?searchid=2502442](http://www.ubuntuforums.org/search.php?searchid=2502442)

Although as alternative I have been using the 64 bit ubuntu version which does not exibit this behaviour for myself so I havn't been looking at this really hard lately.

---

### Post by joerite on 2007-12-16
set iowait to black

---

### Post by joerite on 2007-12-17
I had the same problem on my fresh dual core turion 64 gutsy install. I got powertop to monitor what using power and the restricted broadcom drive was at 99% cause of wakeups-from-idle. So...

Try disabling broadcom restricted driver or figure something further out about that. It worked for me.

---

