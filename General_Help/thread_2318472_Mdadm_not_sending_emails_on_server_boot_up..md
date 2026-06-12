---
title: "Mdadm not sending emails on server boot up."
date: 2016-03-26
forum: General Help
---

### Post by alex522 on 2016-03-26
Hi, 

I followed this guide [here]("http://ubuntuforums.org/showthread.php?t=1185134") to setup madam for monitoring on my RAID array so that I know when the drive fails.

Previously it has been working fine, and still sends emails when I run the test command, however it is not emailing me on startup. Does anyone know where I should start looking? 

I've checked all of the options files in the actual tutorial and they are set correctly.

Thanks.

---

### Post by frostschutz on 2016-03-27
It's hard to help without knowing more about your situation.

If you assemble RAID at early boot before you have networking (usually the case with root on RAID) then you simply won't get an email at this stage. The system has to complete booting and setting up networking first - THEN it should send you a mail IF there is a problem with your RAID.

Do you have a log file for your sendmail/msmtp? You could check it to verify a) whether mdadm tried to send mail at all b) whether there was an error when attempting to send it, because network was not yet available or whatever...

---

### Post by alex522 on 2016-05-16
> **frostschutz said:**
> It's hard to help without knowing more about your situation.

If you assemble RAID at early boot before you have networking (usually the case with root on RAID) then you simply won't get an email at this stage. The system has to complete booting and setting up networking first - THEN it should send you a mail IF there is a problem with your RAID.

Do you have a log file for your sendmail/msmtp? You could check it to verify a) whether mdadm tried to send mail at all b) whether there was an error when attempting to send it, because network was not yet available or whatever...

Thanks, sorry for the late reply. I'd moved to exim4 and upon your suggestion looked at the logs and saw the email request was timing out due toot being able to find the host. The retry time in exim4 was 30 minutes, and after 30 minutes the email would send.

I tried reducing the time to 5m, however the error just keeps repeating itself, until for some reason, it starts working. If I send a manual email to the address, all emails start working no problem.

Any idea why it would still fail to lookup the address until manual intervention or a longer time period?

---

