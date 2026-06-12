---
title: "Cannot wake up from suspend  - Ubuntu 16.04 on Lenovo Z51-70"
date: 2016-04-23
forum: General Help
---

### Post by tpepin96 on 2016-04-23
Whenever I suspend my laptop (which I have disabled in the power options) I cannot wake it up and the fan/computer gets very hot and I need to force a shut down.

How can I fix this or permanently disable suspend functionality

This is the first time I installed Ubuntu on this machine so I do not know if this problem is specific to 16.04.

Added information: The screen automatically turns off when I close the lid most of the way, so I suspect that it is hardware related.

---

### Post by ntinkashyap on 2016-04-24
I am facing a similar issue on my Dell Inspiron 15r. I upgraded from 15.10 yesterday and I have been facing this issue.

I believe the bug report is created at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566302). So we might have to wait till this is fixed.

---

### Post by dFlyer on 2016-04-24
I submitted a bug report for the lid closure suspend. [https://bugs.launchpad.net/bugs/1574161](https://bugs.launchpad.net/bugs/1574161)

---

### Post by alg2 on 2016-04-24
also having the same problem with a Lenovo thinkpad.  I'm still on 14.04.  I'll try upgrading to 15.10 to see if it resolves

---

### Post by ntinkashyap on 2016-04-26
[COLOR=#111111][FONT=Ubuntu]I did a bit of digging and found that this is most likely due to a bug in the 4.4.0 kernel. The problem can be solved when you install the new kernel 4.4.8.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can find instruction to do it here: [http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/](http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/)[/FONT][/COLOR]

---

### Post by tpepin96 on 2016-04-26
That works! 

To fix this, you should upgrade your Kernel as ntinkashyap said to.

Suspending via Power -> Suspend and closing the lid both yield a proper suspend.

---

### Post by matej84 on 2016-10-02
Worked for me! Thanks!

---

