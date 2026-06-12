---
title: "Testing the 3. Version"
date: 2019-04-19
forum: General Help
---

### Post by kanar66 on 2019-04-19
1. Ubuntu 18 which filled my harddisk not doing any further stuff filled it up.
2. Ubuntu Mate same issue this this time 500 GB.
3. Lubuntu 18 dos not fill it up, but on other hand it is for dummys and has no games.
        Its without Software Center (Ubuntu Mate had Earth and only system i had sound:D).
    
Conclusion if Ubuntu I take Ubuntu Mate.
If I can not solve the problem filling HD I would have to reinstall all 5 days, and thats fuss:sad:.
Which software  of Linux does not fill the HD and is suitable for common use?

---

### Post by Impavidus on 2019-04-20
All flavours of Ubuntu are fit for common use and none of them (are supposed to) fill up the hard drive. The only difference is the set of default applications. They all use the same repositories and therefore have the same software available for install.

Can you tell a bit more about your hardware? And if something fills up the hard drive, it's probably something we can solve. The same for not having sound. But it's best to start separate threads for separate issues.

---

### Post by dragonfly41 on 2019-04-20
I would rethink this question ..

> [COLOR=#000000]Which software of Linux does not fill the HD[/COLOR]

[COLOR=#000000]Which game in use fills the HD?[/COLOR]

---

### Post by kanar66 on 2019-04-21
:p looks like i fixed it;)

check; 
Autorotate starts only weekly. So other solution is needed. At least found answers in net.;)cd /var/log
sudo su
> lastlog
> wtmp
> dpkg.log 
> kern.log
> syslog
exit

reboot

This gave me back 190 GB.
Now to know whats be causing (kern.log just ae was 100 GB),
I installed KI Explorer which shows the errors on system.
Workaround was to change grub settings, so the errors stopped and as it is, now it looks perfect.
If you have an error on starting it fills the harddisk as it never stops retrying.

Just I have to tell the problem started with the upgrade to a newer kernel on system.
Conclusion be careful upgrading new kernel.

---

### Post by TheFu on 2019-04-21
Or better, fix errors with the system.  It took a full disk to get attention.  Some monitoring would be helpful.  I use logwatch to have the logs monitored daily and get notified of any issues.

Deleting primary log files is a poor solution. There could be hack attempts and other issues listed in those files.

OTOH, I size my OS to be 20-25G, so the issue would never become 190G worth of a problem.

---

