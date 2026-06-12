---
title: "ndiswrapper not loading"
date: 2007-07-21
forum: General Help
---

### Post by The Judderman on 2007-07-21
Hello!

I have a bcm 4306 which has been working absolutely fine until today with ndiswrapper. I had a notification of updates, which I blindly followed, without really noticing what they were, and on reboot, ndiswrapper is not loading. Looking at the recovery mode, I get the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-12-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument (which I also get from modprobe ndiswrapper)

and I can't access my wifi.

interestingly, I also get these outputs:

[INDENT]peter@laptop:~$ sudo ndiswrapper -i driver.inf
driver driver is already installed
peter@laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

peter@laptop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
driver : invalid driver![/INDENT]

Any ideas?

Please help!!!

I have been thinking of doing a fresh install using Feisty, so now might be the time to do it, but if you have any ideas, they would be well received!!

Cheers!

The Judderman

---

### Post by The Judderman on 2007-07-21
For people's info incase they have the same problem, I basically just reinstalled ndiswrapper, and did modprobe ndiswrapper and rebooted, and hey presto, I'm connected with my wifi!!!!

Follow this link for a fantastic how to with ndiswrapper and bcm4306!
[http://ubuntuforums.org/showthread.php?t=340689&highlight=HOW+TO%253A+Broadcom+4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=HOW+TO%253A+Broadcom+4306)

Cheers!

The Judderman

---

