---
title: "automated upgrade vs package errors"
date: 2020-07-17
forum: General Help
---

### Post by Skaperen on 2020-07-17
i have experienced 2 times when doing an upgrade resulted in a system that would not run right (something in a library crashed most executables) or a system that would not finish coming up (i/o activity stopped and the CPU fan went idle suggesting something was waiting for something that would never happen).  i was able to do another upgrade a couple days later and the problems went away ... **sHiFt HaPpEnS** ... now i am thinking about this for _a server i want to have_ *keeping itself upgraded*.  the risk is that after an upgrade there could be some level of failure that might well be fixed at some point in the future (time probably inverse of the exponent of how serious the problem is).  what i am wanting to do is have a means to detect most failures and hold off the upgrade until there is success sustain for some defined time period (susfixminsec).  *are there any projects aimed to do this or am i getting into fresh grass?*

---

### Post by franknfurter2 on 2020-07-17
Dear Skaperen,

sounds mystic to me, what you are reporting. I run ubuntu for years now and only had one situation where I had to set up the system anew. That happened because I did not read the documentation of what I am trying to do very well. So it was my fault. > i/o activity stopped and the CPU fan went idle suggesting something was waiting for something that would never happen) sounds like a process that's taking the whole performance of the system. Normally one can find the relevant process by using top.

If you are worried that your system gets damaged by updates, it is always a good idea to make a backup before an update. Virtualization is a good idea here as well. Virtualize your server, take a snapshot before the update, run the update and do your tests. When tests ok delete the snapshot. Why do you not go this way?

Regards

Frank

---

### Post by Skaperen on 2020-07-17
this is *not* a case of me goofing up the install.  i really have done that before because i do dabble around with it a lot.  the most common is not having enough space.  i also try to apply my mods and package changes.  i have worked out good ways to do that.  i always make triple backups and know i can just boot a USB memory stick (i no longer use CD/DVD any more, and the only such drive i have is an external USB one i have not used since 2013 and have no idea where it is) and get a system up and running enough to resume dabbling.

this is a case of an upgrade (like: apt-get update && apt-get -y upgrade) resulting in what looks like an OK system that fails as described in post #1.  there was something bad in the upgrade in 2 occasions, and it was not a kernel issue (kernel was not upgraded).  i don't have an issue with this as i have the whole system backed up in reverse increments (a space saving way to do backups that can be restored to a desired backup date).  i can restored the system to about a week before while leaving /home, /home2, and /var unchanged (they are backed up bu i can elect to not restore them).  i can undo the upgrade.

now i am doing this in the cloud.  a lot of things are done differently.  but one i have a system running as i want, upgrades are basically the same. 

i want to automate the upgrade and reboot.  i already have a work queue that lets me doing specified things around a series of reboots.  i have done upgrades this way by just starting a script and eating dinner.  when i am done, i have an upgraded, freshly booted system ready to use.  it rebooted (so the upgrade runs on a freshly booted system), upgraded, waited 3 minutes, rebooted, waited 3 minutes again (this part when any package that finishes after reboot gets to do its thing), rebooted a 3rd time, runs my script to start my system up my way and autologin about 17 users.  the system i want to fully automate is a cloud server.

i want to be sure a bad upgrade does not disable the intended services.  things will be done in a few minutes "for maintenance" at a not so busy time.  i want to be sure it comes back up.

---

### Post by franknfurter2 on 2020-07-19
Dear,

what I did understand until now is, that you what to be sure, that the services of your cloud server are still working after an automatic upgrad and reboot of the system. And here is my opinion for that:

You can never be sure, that an upgraded system works afterwards. There is no 100% guarantee for that. Who should give this guarantee? The only thing you can do is to establish a watchdog process on another system that observes the upgrade and services and does a automatic rollback of the system in case of a failure.

Regards

Frank

---

### Post by Skaperen on 2020-07-20
that sounds about right.  what i am looking for is something that has been put together to do that, or at least some suggestion details.

---

