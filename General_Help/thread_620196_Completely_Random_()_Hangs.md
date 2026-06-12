---
title: "Completely Random (?) Hangs"
date: 2007-11-22
forum: General Help
---

### Post by Dragon45 on 2007-11-22
This is a completely unhelpful topic title - but that's because I genuinely can't find a correlation between hangs and any particular activity. The first time Ubuntu hung (about a month and a half ago), it was on my screensaver (Helios). The second time it hung, I was surfing the web with Firefox (yesterday). The third time (today), I was in terminal and it went to screensaver and hung after some time.

I have a pretty vanilla OpenSSH/LAMPP (thats Python and PHP, not Perl, 'natch 8) ) setup on a several-month old Gateway MA7. I started tinkering with Xen and Qemu recently and I think that may have increased the likelihood of hangs occuring, but I really can't be sure. 

Questions:

1) What is the general debugging methodology in Ubuntu for such issues (logs, debugging processes, what) ?

2) Is there a possibility that my OpenSSH setup (password, not key-based, login) means that I have been rootkitted or 'pwned' in some other manner (unlikely, no unusual process spikes I can remember, no undesired network usage I can recall getting... but still...)

Thanks for the help.

-Dragon45

---

### Post by Dragon45 on 2007-11-22
I forgot to add that I'm running Gutsy, with no updates pending that I can see.

Also, it just hung again. I realized the last common thread between all of these crashes is Firefox + Youtube open either in the foreground or the background. Flash does screw up Firefox fairly regularly (expected), but I wonder if anyone else has been having serious, system-wide stability issues with it since upgrading to Gutsy?

---

### Post by tim1 on 2007-11-22
I experience random hangs toom but usually several times a day, so consider youself lucky.

I reporte this bug:
[https://bugs.launchpad.net/ubuntu/+bug/159398](https://bugs.launchpad.net/ubuntu/+bug/159398)

There are other threads in this forum with lots of  where users report similar problems, but so far no Ubuntu developer said anything about the issues.

I regret upgrading to Gutsy so much, my computer is basically not usable.

---

### Post by zippy028 on 2007-11-23
Many people experience this issue some were able to remedy the freezes by installing an older version of the Nvidia driver. This worked in my situation when I installed version 100.14.09. 

HTH,
John

---

