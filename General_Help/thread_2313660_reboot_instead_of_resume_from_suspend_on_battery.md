---
title: "reboot instead of resume from suspend on battery"
date: 2016-02-14
forum: General Help
---

### Post by xjin2 on 2016-02-14
Hi, after recent updates, I am facing the exactly the same problem as described here: 
[http://unix.stackexchange.com/questions/252679/asus-ux303ua-rebooting-instead-of-resuming-from-suspend-ubuntu-15-10/253901](http://unix.stackexchange.com/questions/252679/asus-ux303ua-rebooting-instead-of-resuming-from-suspend-ubuntu-15-10/253901)

That is, on AC power, suspend and resume without problems. But when either suspend or resume is done on battery, the resume part becomes a reboot. I cannot find anything useful in syslog.

The poster on stackexachange seems to have solved the issue by updating the kernel. However, for all kernel versions I tried (4.2.0-27, 4.2.0-25, 4.2.0-23), the problem persists.


Any ideas or similar situations?

---

### Post by sandyd on 2016-02-14
There have been some issues in various laptops that cause this, such as [https://bugs.launchpad.net/linuxmint/+bug/1390923](https://bugs.launchpad.net/linuxmint/+bug/1390923)

What laptop model are you using, and does it use intel graphics?

---

### Post by xjin2 on 2016-02-15
Thanks for the reply. I am using XPS15 with GTX960M (with official non-free driver).

That bug report you mentioned was a year ago. Could it be related? Suspend and resume worked perfectly fine before recent updates (I only started noticing this issue this week).

---

### Post by xjin2 on 2016-02-18
Any new ideas?

---

### Post by xjin2 on 2016-02-18
This is extremely strange. Just now I decided to disable xfce powermanager so that it won't be on battery mode. And indeed even on battery suspend and resume worked. 

The magical thing is, after I reenable the powermanager, suspend and resume still work on battery! I have completely no idea what happened.  Right before I disabled the powermanager, I tested it several times (with all available kernel versions) and they all failed. So it's definitely not due to any system updates.

I'll see whether this magic persists after days.

---

