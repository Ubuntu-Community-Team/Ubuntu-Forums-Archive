---
title: "Software Updater"
date: 2015-12-11
forum: General Help
---

### Post by pfeiffep on 2015-12-11
I have 2 machines that behave differently wrt Software Updater. Beside the obvious System Settings | Software & Updates where else can I explore so that the behavior is similar?

The difference in behavior I notice is on my Dell laptop the updater doesn't notify me when updates are available, and on my HP desktop the notification happens as I have configured. 

Both machines have 64bit 14.04 LTS installed, both have gnome flashback, and have a very similar software complement. The HP is hardwired to my router, the Dell uses wifi to connect. 

This is a _SLIGHT_ annoyance for me ... after I notice the HP prompting the next time I use the Dell I manually run the updater. 

TIA

---

### Post by grahammechanical on 2015-12-11
I have two installs of 16.04 (development version) on the same machine and the development version has daily updates but each install gets updates to different packages. This is life. In your case it might also be phased updates.

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Update the same package to every user and if the update introduces a regression bug then every  user is affected. Push the update to a certain percentage of users and if anyone screams hold back the update for the rest of the users until the problem is fixed. If nobody screams then push out the update to another percent of users and so on until all users have the update and few users have been affected by any regression bugs.

If you want the risk of a major annoyance then run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The command apt-get dist-upgrade will bring in all the updates that are being held back. It is said to do this in a "smart" way by removing packages that cause conflicts. I have known dist-upgrade to break things.

Recently I had 171 packages held back on one install of Xenial Xerus including a kernel upgrade and none held back on the other install which already had the newer kernel (4.3). So, I ran dist-upgrade, restarted with my fingers crossed and I got low screen resolution. I changed proprietary video drivers and that fixed the low screen resolution.

I share my experience with you.

Regards.

---

### Post by pfeiffep on 2015-12-11
Thanks for your response grahammechanical.

I've not really paid attention to any holdbacks (once I adopted LTS software updater is my preferred method vs apt command line) My concern is a security update might be missed on the Dell since the updater doesn't seem to run.

I'll pay increased attention on the HP for any security updates so I can wait a week or so to manually running the updater on the Dell (letting PhasedUpdates catch the Dell)

---

### Post by ian-weisser on 2015-12-11
> **pfeiffep said:**
> on my Dell laptop the updater doesn't notify me when updates are available

Check the configuration,
Check the logs in /var/log
Check /var/log/syslog for errors with cron.daily. apt has a daily job that triggers (amongother things) Software Updater.
Check that you don't have the unattended-upgrades package installed. It will install many updates without triggering Software Updater.
You can always try reinstalling update-manager, the package that provides Software Updater.
.

---

### Post by pfeiffep on 2015-12-11
Thanks for your response> **ian-weisser said:**
> 

Check the configuration,
Check the logs in /var/log
Check /var/log/syslog for errors with cron.daily. apt has a daily job that triggers (amongother things) Software Updater.
Check that you don't have the unattended-upgrades package installed. It will install many updates without triggering Software Updater.
You can always try reinstalling update-manager, the package that provides Software Updater.
.
Configuration is the same, and no unattended upgrades
I'll check the logs for errors during the next week, if none found will consider reinstalling update-manager.

---

### Post by ian-weisser on 2015-12-11
Correction: Try reinstalling update-notifier instead of update-manager.

---

### Post by pfeiffep on 2015-12-14
Well no need to re-install update-notifier:p
Software updater just ran on my Dell ... I suppose that I was just impatient

---

