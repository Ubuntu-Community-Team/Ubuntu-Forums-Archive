---
title: "[something] has been mounde 30 times without being checked, check forced. ... failed"
date: 2007-01-28
forum: General Help
---

### Post by Ragzouken on 2007-01-28
Using Ubuntu Edgy Eft

I got a message like this when I booted up:
[something] has been mounted 30 times without being checked, check forced
I wasn't really paying attention but noticed  '[[COLOR="Red"]fail[/COLOR]]' before it ended and began to boot Ubuntu.

Now the classic signs of ubuntu being broken on my system are showing: Sound plays nothing but a continuous note and the taskbar/panels are laggy and slow for a while after boot and terminal and gedit (actually everything under Applications > Accessories it seem to be) are very slow to load. (These things seem to always happen when something has gone wrong, mostly when I've messed up the xorg.conf)

Can anyone help me find what is causing this problem, know what it is, or even help me fix it? Also I'm interested to know why those certain things always happen when stuff goes wrong if anyone knows.

---

### Post by Puschkin on 2007-01-30
> [something] has been mounted 30 times without being checked, check forced
This means that one of the partitions of your harddrive is being checked for errors.

It happens when you mount (load) the partition 30 times and it hasn't been checked since.

The bad thing is that the test fails on your system. Sometimes it fails when you turn the computer off without shutting it down properly, but in your case your harddrive might have been damaged (slow, laggy).

Try to find tutorials on how to use the commands: "badblocks" and "fsck", these are tools to verify the integrity of your harddrive and partitions.

Hope this helps.

Greets,
Puschkin

---

