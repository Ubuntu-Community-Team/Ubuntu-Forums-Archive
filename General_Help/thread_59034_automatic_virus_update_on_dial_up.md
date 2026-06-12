---
title: "automatic virus update on dial up?"
date: 2005-08-22
forum: General Help
---

### Post by Monkey_See on 2005-08-22
Hello,

I'm setting up a basic ubuntu box to use as a samba server (basic file and print sharing) to a small number of windoze machines.  Everything works perfectly, my only problem is that that the only connection to the internet is through dial up, and I'm having trouble automating the process of dialing up and downloading new virus definitions.

I can do it manually by going:

```
sudo wvdial

sudo /usr/local/f-prot/tools/check-updates.pl
```
I though that I would be able to just set up a cron job to do this for me by adding the following into /etc/crontab

```
5 3    * * 7   root    wvdial
8 3    * * 7   root    /usr/local/f-prot/tools/check-updates.pl
```
However these entries show up in my syslog and auth.log, but nothing appears to happen?

If anyone could point me where I'm going wrong, or suggest a better way I would most appreciate it.

Thanks,
Monkey_See

---

### Post by Monkey_See on 2005-08-24
OK, so I figured it out and if anyone is interested this is how I managed:

Instead of using wvdial I used pon after setting up the dialup connection using pppconfig.  I set the idle timeout for 180 seconds so the connection won't stay up all morning when the virus definitions have been completed (thou with dialup it will likely take all morning anyway).

and my /etc/crontab additions look like this:

```
5 3    * * 7   user    pon ISP
8 3    * * 7   root    /usr/local/f-prot/tools/check-updates.pl
```
where user is my user name, also it could be root, though I found if I wanted to stop the connection I would have to use a sudo poff.

Thats it...it works.

Hopefully this can be helpful to someone.

---

