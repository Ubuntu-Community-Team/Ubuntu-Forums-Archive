---
title: "Boot Failure"
date: 2014-12-07
forum: General Help
---

### Post by orsome1 on 2014-12-07
I am very new to Ubuntu and use the Ver 12.04 LTS to run my HT PC
Has been running well for months but now having boot up problems. If I shut the server down and then try reboot it stops on a black screen and wont boot further - I have to switch off and on again and then boots up ok.

I was thinking of trying to upgrade to 14.04.1 but after seeing the number of errors experienced by others I am very nervous to.

Is there a way to detect what the problem is that is halting the boot up process randomly like this? and to correct 

If I do upgrade to 14.04.1 will all my current settings be unaffected like samba server, NUT, drive mountings etc.

It took me months of struggling to get all set up so I really dont want to go through that again

---

### Post by nerdtron on 2014-12-07
> Is there a way to detect what the problem is that is halting the boot up process randomly like this? and to correct

You might want to look at the logs after the successful boot.
Some file to look at under the /var/log/ directory are the dmesg, kern.log, boot.log and syslog

> If I do upgrade to 14.04.1 will all my current settings be unaffected like samba server, NUT, drive mountings etc.

It took me months of struggling to get all set up so I really dont want to go through that again
Don't upgrade to 14.04 using the "dist-upgrade" command or using the software updater. This update can be a hit or miss depending on your hardware and application setup. A better way to upgrade is a clean install, but you'll need to setup your services again.

---

### Post by orsome1 on 2014-12-08
had a brief look at the logs but not quite sure what I am looking at. There are two files for each of the logs.

---

