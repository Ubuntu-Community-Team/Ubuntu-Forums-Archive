---
title: "Unable to get root cronjob to run"
date: 2016-12-14
forum: General Help
---

### Post by blomstertj on 2016-12-14
I've used gnome-schedule to make a simple cronjob for my own user but it doesn't seem to make a good one for root.  So I tried to make one myself.  I've used the terminal command: ```
sudo crontab -e
```

and from what I've read this should work but the command does not run.  This won't the real time but I'm just trying to make sure it runs at the time I put it at.  I've tried just /sbin/reboot but it does not execute.  What am I doing wrong here?

```

PATH=/sbin:/bin:/usr/sbin:/usr/bin
Home=/

46 11 * * * root /usr/sbin/reboot


```

---

### Post by deadflowr on 2016-12-14
Try changing it to /sbin/reboot
I don't see /usr/sbin/reboot.

---

### Post by blomstertj on 2016-12-14
> **deadflowr said:**
> Try changing it to /sbin/reboot
I don't see /usr/sbin/reboot.

changing it has no effect.  Is my testing method bad? Does cron need a while to like update its job list or something?  So at 2:32 I created the job and set the time to a few minutes later to see if it works.

Anyways this is my code with your change.
```

PATH=/sbin:/bin:/usr/sbin:/usr/bin
Home=/

38 14 * * * root /sbin/reboot



```

---

### Post by steeldriver on 2016-12-14
You don't need the username (root) in cron jobs run using root's crontab - that syntax is only for jobs listed under /etc/cron

It will be trying to run root as a command

---

### Post by blomstertj on 2016-12-14
> **steeldriver said:**
> You don't need the username (root) in cron jobs run using root's crontab - that syntax is only for jobs listed under /etc/cron

It will be trying to run root as a command

That did it, thank you.  In case anyone was wondering, I basically am trying to reboot into Windows using the grub-reboot command so Windows can run Windows update and optimize my drives.  I only run Windows 10 for PC gaming.

---

