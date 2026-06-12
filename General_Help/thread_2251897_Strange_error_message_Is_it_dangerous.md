---
title: "Strange error message Is it dangerous?"
date: 2014-11-07
forum: General Help
---

### Post by Gnusboy on 2014-11-07
Hi All

I am seeing an error code on boot and need to know what it is and what might happen.  [ 0000:00:18.3 ] Unreliable thermal sensor monitoring disabled

It happened once or twice before, and the first time the code was [12.003397] 1: 10 temp unreliable cpu thermal sensor monitoring disabled

I saw the message a few days ago as well. Once when booting into 12.04 and then today booting into 14.04

I recently upgraded to Ubuntu 14.04 installed next to Ubuntu 12.04. 

Is it a warning of CPU failure? Could it be something else?

Thanks in advance

---

### Post by Gnusboy on 2014-11-07
> **Gnusboy said:**
> Hi All

I am seeing an error code on boot and need to know what it is and what might happen.  [ 0000:00:18.3 ] Unreliable thermal sensor monitoring disabled

It happened once or twice before, and the first time the code was [12.003397] 1: 10 temp unreliable cpu thermal sensor monitoring disabled

I saw the message a few days ago as well. Once when booting into 12.04 and then today booting into 14.04

I recently upgraded to Ubuntu 14.04 installed next to Ubuntu 12.04. 

Is it a warning of CPU failure? Could it be something else?

Thanks in advance

******************************************************


I think I did not write the error code correctly. Todays message showed [ 0000:00:1 k8.3: ] Unreliable thermal sensor monitoring disabled

The previous message showed [12.003397] 1: 10 temp unreliable cpu thermal sensor monitoring disabled

Sorry for the confusion.

My system: AMD Quad core Phenom

4 GB ram and 600 GB hard drive

This is what I get from Syslog I don't know if it is important or not

Nov  7 09:08:16 Ranha rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="491" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Nov  7 09:10:19 Ranha anacron[1037]: Job `cron.daily' terminated (mailing output)
Nov  7 09:10:19 Ranha anacron[1037]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 255
Nov  7 09:10:19 Ranha anacron[1037]: Normal exit (1 job run)
Nov  7 09:17:01 Ranha CRON[2661]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by coldcritter64 on 2014-11-07
On my desktop CPU, AMD 9750 Phenom X4 (quad core) I've been seeing that error on ubuntu and debian installs for quite a long time now without any failure. I can't guarantee that a failure won't happen, though the warning doesn't actually sound that bad to me.

With thermal sensors being built into the mainboard and cpu, it seems the OS can't use them (reasons unknown / not stated) it seems it just turns them off if they can't be used and notifies you. It hasn't affected my use of the systems on that hardware and I can still monitor the CPU temp / GPU temp with lm-sensors, though I haven't been able to monitor voltages etc with lm-sensors since I've been seeing that error. Maybe the manufacturer does not use linux supported hardware components for some of the sensors, I really don't know why.

Reading those syslog entries, I don't think they are related to sensors at all (cron and mail warnings, cron is a job scheduler in linux).

---

### Post by evilbrent on 2014-11-07
Either way it's time to make sure your backups are in order...

---

### Post by Gnusboy on 2014-11-07
Thanks. It may be just a bug, but it's a new thing. Hadf not seen it until this week

---

### Post by Gnusboy on 2014-11-07
Yup. I made full back ups of 12.04 before I upgraded to 14.04. They  are on a external drive, so I'm not too worried. I really don't want to build a new system just yet. Blah!

---

### Post by coldcritter64 on 2014-11-07
> **evilbrent said:**
> Either way it's time to make sure your backups are in order...

It has been that time for near 18 months now for me with that particular warning. I keep my personal data I want protected on a separate drive and occasionally take dd or tarball "snapshots" of the root partition and home partition, my usual backup routine (though not really done routinely enough :-))  


Check out this link [http://ubuntuforums.org/showthread.php?t=2222109](http://ubuntuforums.org/showthread.php?t=2222109), posts #4,6 & 8 by QIII. It may help you relax a bit more about the warning with that info. Cheers

Edit: I thought while posting this I was referring to the OP, just noted it was another member :lol:. @OP, check the link it may help you a bit.

---

