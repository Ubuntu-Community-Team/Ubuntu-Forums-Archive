---
title: "dvbstream filling up logs"
date: 2008-04-23
forum: General Help
---

### Post by rm-digital on 2008-04-23
I have been using dvbstream to record from a DVB-T card on Ubuntu 7.10. This has been working fine for weeks, but just recently the syslog, kern.log and messages files in /var/log have been filling up rapidly while dvbstream is running.

This is the kind of thing going into these log files:

Apr 23 19:11:59 ceti kernel: aea0d0
Apr 23 19:11:59 ceti last message repeated 2 times
Apr 23 19:11:59 ceti kernel: <4aea0d8
Apr 23 19:11:59 ceti kernel: aea0d8
Apr 23 19:11:59 ceti kernel: aea0d8
Apr 23 19:11:59 ceti kernel: aea0d8aea0d8
Apr 23 19:11:59 ceti kernel: aea0d8

 and:

Apr 23 19:12:12 ceti kernel: [ 1236.310180] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310202] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310224] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310251] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310274] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310296] bt878(0): irq PPERR risc_pc=1faea0d0
Apr 23 19:12:12 ceti kernel: [ 1236.310322] bt878(0): irq PPERR risc_pc=1faea0d0

the same entries appear in all three of these log files and this causes these log files to fill up at a similar rate to the file dvbstream is recording to. As a result disk space is being used up at 4 times the rate it should be and I have to keep deleting the logs.

The recorded TV programme is fine.

I hadn't changed any settings on my system recently. I had installed some updates but these seem to be related to apt-get, avahi, poppler, network manager, and update manager. None of these seem to have any relation to dvb applications as far as I can tell.

Does anyone have any idea why this might have started happening and how I can stop it?

---

