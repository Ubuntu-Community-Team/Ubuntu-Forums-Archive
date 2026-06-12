---
title: "ubuntu dapper locking up?"
date: 2007-04-20
forum: General Help
---

### Post by 95aspire on 2007-04-20
hey guys ive noticed lately my server has been locking up for no reason, how can i determine the problem?

---

### Post by tgalati4 on 2007-04-20
We'll need a little more information.  How about logging in from another computer via ssh?  You can run snapshops of the system with a cron job that captures the system state every 5 minutes or so (ps -ef > whatisrunningonmymachinerightnow.txt)

Could be a memory problem.  Boot with a live disk, go to options, run memtest overnight.  Try reseating your memory.

 I blew the dust out of a Dapper system after 6 months of continuous use.  Temperatures dropped 5 degrees C.  I was getting system slowdowns because of thermal throttling.  You could see it on the thermal monitor plots.  I had the throttling set at 50C, now I have it set to 52C.  It appears to be locked up, but it could be running slowly.

Check the voltage on your 5V and 12V supplies.  A wonky power supply can cause harddisk read problems which can lock up the bus.

Check dmesg.  Check all of your log files in /var/log.  You will probably find some symptoms.

Did you do any updates lately?  If not, then I would bet a hardware problem.  Dapper has been pretty stable for me.

---

### Post by 95aspire on 2007-04-20
ill try to blow it out tonight in a bit,as far as i know no updates have been installed and whatnot, 

ill try memtest as well 

but its just an old emachine 600is series computer, a celeron proc 600mhz, 256mb ram, etc. 

ill also use my tester on the psu tonight as well, was thinking its hardware but wanted a second opinion lol, as its ran stable for a cpl months now so could very well be a dust problem

---

