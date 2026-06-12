---
title: "Cron-ing a script that Upstarts a service"
date: 2008-04-15
forum: General Help
---

### Post by robacarp on 2008-04-15
I am writing a script to automatically copy files from a USB drive, when present.  At the end of the copy process, I need to restart an Upstart service.  Being as that the script runs when the USB drive is present I just set the script to run in cron every minute and look for the drive.

The script works fine when run directly from the terminal.  When USB is inserted or not, it does what it is supposed to.  It even restarts the Upstart service as needed. 

But when I run it from a crontab, it fails to restart the service.  Everything else works great....but not the service.  

I even tried something as simple as:
```
* * * * * stop serviceName > /var/log/crontest.log
```
with the service already running.  It doesn't stop.  The opposite is true (swapping stop for start, the service never starts).  Nothing comes out in the log...at all.

Any ideas?  Unfortunately google is of almost no help because upstart is so new...

Thanks, Robert

---

### Post by robacarp on 2008-04-15
Bump.   Man this forum gets a lot of activity....

---

### Post by robacarp on 2008-04-15
[solved]  Through some great detective IRC work by Sipior 

Apparently if a cron needs to be executed as root, this does not work: ```
sudo -s
crontab -e
```

Although it is still added under roots crontab ( /var/spool/cron/crontab/root ) it does not have complete root privileges.   It does have some though (ability to mount/unount, for instance).

What worked instead was to add the cron job manually to /etc/crontab with root as the executing user.

---

