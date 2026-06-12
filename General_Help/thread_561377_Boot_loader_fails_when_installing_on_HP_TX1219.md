---
title: "Boot loader fails when installing on HP TX1219"
date: 2007-09-27
forum: General Help
---

### Post by santosh_n on 2007-09-27
I'm trying to install Ubuntu using Wubi on my HP TX1219 laptop. I already have Vista installed on C drive and am installing Wubi/Ubuntu on C drive.

The initial Wubi installation goes through fine and it reboots and starts installing Ubuntu.

After the installation completes and it boots into Ubuntu I got the Ubuntu logo and the status bar. However after the status bar went up to about 40% the system froze. I waited for a long time but nothing happened. I then restarted the laptop and this time it froze on the initial boot screen itself.

I had to again restart the laptop. After I did that the laptop refuses to boot and gives me a 'boot configuration file error'.

I would appreciate if anyone could help me with some pointers on how to resolve this issue.

Thanks,
Santosh

---

### Post by ago on 2007-09-27
If you hard reboot, you may have to use chkdsk /r from a windows CD

Once that is done, press alt+f1 while booting Ubuntu to see more messages and pinpoint the issue.

---

### Post by clive_pearce on 2007-09-27
I'm new to Ubuntu. But I think the message 'boot configuration file error'
points to grub not being installed correctly, & I think you need to run fixmbr from the recovery console.

Good Luck

---

