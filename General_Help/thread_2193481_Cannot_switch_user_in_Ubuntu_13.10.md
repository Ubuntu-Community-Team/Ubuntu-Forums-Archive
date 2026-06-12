---
title: "Cannot switch user in Ubuntu 13.10"
date: 2013-12-13
forum: General Help
---

### Post by ICouldBeAnyone on 2013-12-13
I have run an upgrade on our main computer (fresh install) but now it sometimes won't switch user. from the lock screen, if you press switch user you get a blank screen, then you come back to the lock screen. and from the power menu, when you try to switch user nothing at all happens. I can log out fine but I can't switch user. this is getting very annoying. any ideas?

Thanks in advance!

---

### Post by eldrich_rebello2 on 2013-12-13
do you have another user account set up? This might be helpful: [http://askubuntu.com/questions/379485/problem-changing-users-in-ubuntu-13-10](http://askubuntu.com/questions/379485/problem-changing-users-in-ubuntu-13-10)

---

### Post by ICouldBeAnyone on 2013-12-16
Yes the computer has three users. I was using nvidia-319-updates because nvidia-319 wouldn't let you switch user at all. At least with "updates" you could sometimes switch user. I tried going to the open source driver but now x.org crashes all the time, this is our main computer and I need to get this fixed.

Thanks for your help so far!

---

### Post by spazzeri on 2014-01-29
Have you solved the problem ?

---

### Post by brlewis on 2014-03-05
I have the same problem on my Thinkpad T510.

---

### Post by sammiev on 2014-03-05
> **brlewis said:**
> I have the same problem on my Thinkpad T510.

Hi brlewis, I would start a new thread if I were you. You will likely get more help.

---

### Post by spazzeri on 2014-03-06
Watch this critical bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1247189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1247189)

---

### Post by spazzeri on 2014-03-18
Have a look at this answer on askubuntu.com:
[http://askubuntu.com/a/421880/1780](http://askubuntu.com/a/421880/1780)

I replaced lightdm with gdm, and now I can happily switch users in 13.10

---

