---
title: "ntpd cron job permission denied"
date: 2008-03-10
forum: General Help
---

### Post by lodbot on 2008-03-10
First forums post, though I've been leeching a lot.

I'm running 6.06 and I followed this guide on how to synchronize time with NTP (for 7.10) - [https://help.ubuntu.com/7.10/server/C/NTP.html](https://help.ubuntu.com/7.10/server/C/NTP.html).  The guide works great when I run everything manually with sudo, but the cron job doesn't work - my system time continues to get out of sync.  I followed the guide perfectly and did a bunch of searching to track down the problem.  It appears as though ntpdate needs to be run by root.  Take a look:

```

$ ntpdate ntp.ubuntu.com pool.ntp.org 
10 Mar 05:02:55 ntpdate[671]: bind() fails: Permission denied
$ sudo ntpdate ntp.ubuntu.com pool.ntp.org 
10 Mar 05:03:14 ntpdate[672]: adjust time server 209.132.176.4 offset 0.062731 sec

```

How do I go about solving this problem?  Is there a way to run a cron job as root?  Can I configure ntp differently so that I don't need to be root (sounds like a bad idea)?  From others' posts, I learned that perhaps ntp needs to be running all of the time?  When I **$ ps aux | grep ntp** I get nothing.

Thanks ahead of time.

---

### Post by jakev383 on 2008-03-10
If you setup ntp-server, it will sync all the time - you don't have to allow others to sync from you, but the same package will keep your system sync'ed.
Otherwise you could look at allowing the user who runs cron jobs (I'm assuming your user) sudo access to ntpdate.
How did you create the cron job? Did you create it as your user, or as root? Or did you write a script and drop it in /etc/cron.hourly?

---

### Post by lodbot on 2008-03-10
> **jakev383 said:**
> If you setup ntp-server, it will sync all the time - you don't have to allow others to sync from you, but the same package will keep your system sync'ed.
Thanks for the heads up; I'll start fiddling with ntp-server.

> **jakev383 said:**
> Otherwise you could look at allowing the user who runs cron jobs (I'm assuming your user) sudo access to ntpdate.
How did you create the cron job? Did you create it as your user, or as root? Or did you write a script and drop it in /etc/cron.hourly?
I created the script exactly how the guide told me to.  I created a file in /etc/cron.daily called ntpdate that runs the command (without sudo) that I listed previously.  I created the file with my user, but chowned it to root:root and chmodded it to 755.  I haven't tried changing the script to run the command with sudo, because I'm assuming things will break (not sure what would happen if a cron job needed a password).  Is there a different way to setup my cron script that will avoid these permission errors?

I'll also look into giving sudo access to my user for ntpdate.  Thanks for the response!

---

### Post by ajgreeny on 2008-03-10
Simply right click in your clock on the panel and go to Adjust time and date, and from there you can set up to sync your time with the ntp servers nearest you, or anywhere in the world if you want.  By default ubuntu is set to sync with the ubuntu servers so you don't need to change anything if you don't want to.

---

### Post by lodbot on 2008-03-10
> **ajgreeny said:**
> Simply right click in your clock on the panel and go to Adjust time and date, and from there you can set up to sync your time with the ntp servers nearest you, or anywhere in the world if you want.  By default ubuntu is set to sync with the ubuntu servers so you don't need to change anything if you don't want to.Thanks for the reply, ajgreeny.  I don't have a GUI installed, so I can't right click.

EDIT: fixed a small typo.

---

### Post by Oldsoldier2003 on 2008-03-10
> **lodbot said:**
> First forums post, though I've been leeching a lot.

I'm running 6.06 and I followed this guide on how to synchronize time with NTP (for 7.10) - [https://help.ubuntu.com/7.10/server/C/NTP.html](https://help.ubuntu.com/7.10/server/C/NTP.html).  The guide works great when I run everything manually with sudo, but the cron job doesn't work - my system time continues to get out of sync.  I followed the guide perfectly and did a bunch of searching to track down the problem.  It appears as though ntpdate needs to be run by root.  Take a look:

```

$ ntpdate ntp.ubuntu.com pool.ntp.org 
10 Mar 05:02:55 ntpdate[671]: bind() fails: Permission denied
$ sudo ntpdate ntp.ubuntu.com pool.ntp.org 
10 Mar 05:03:14 ntpdate[672]: adjust time server 209.132.176.4 offset 0.062731 sec

```

How do I go about solving this problem?  Is there a way to run a cron job as root?  Can I configure ntp differently so that I don't need to be root (sounds like a bad idea)?  From others' posts, I learned that perhaps ntp needs to be running all of the time?  When I **$ ps aux | grep ntp** I get nothing.

Thanks ahead of time.
put it in roots crontab

this is what my root crontab looks like:
```
1 3 * * *       ntpdate ntp-1.mcs.anl.gov
5 3 * * *       hwclock --systohc
15 3 * * 6      slocate -u
```

---

### Post by ajgreeny on 2008-03-10
Sorry, I didn't notice it was a server!

---

### Post by lodbot on 2008-03-10
> **Oldsoldier2003 said:**
> put it roots crontabI'm not really sure what you mean ...  Is there a certain crontab for root?  How do I modify this crontab?  I don't see anything in /etc.

---

### Post by Oldsoldier2003 on 2008-03-10
> **lodbot said:**
> I'm not really sure what you mean ...  Is there a certain crontab for root?  How do I modify this crontab?  I don't see anything in /etc.

```
sudo -i
```

create a file for roots crontab, name it root.cron (or whatever you want)

still as root:

```
crontab -u root <nameof the crontab>
```

---

### Post by lodbot on 2008-03-10
Here's a log of what I did for others' reference:
```

$ cd /etc
$ sudo emacs cron.root
-- only contains: 25 6    * * *   root   ntpdate ntp.ubuntu.com pool.ntp.org
$ sudo crontab -u root cron.root

```

I'll give it a few days and see how that clock is doing.  Thanks for the help!

---

