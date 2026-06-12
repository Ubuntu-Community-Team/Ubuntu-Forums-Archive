---
title: "Smartmon Tools - MSMTP Emailing Issue/Question"
date: 2013-02-21
forum: General Help
---

### Post by mosscomes on 2013-02-21
I'm trying to configure an Ubuntu file server (12.04LTS) with smartmon tools to e-mail hard drive alerts. I'm using msmtp, on which I can receive test messages from the command line. When I try to send a test message via smartmon tools, it doesn't work. Thinking I needed one more piece in the mix, I added heirloom mailx, configured it and received a test mail. It still doesn't work when I try to send a test message through smartmon tools.

The syslog on this error keeps saying:

Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root: successful Feb 21 09:14:03 Ubuntuserver smartd[8677]: Executing test of /usr/share/smartmontools/smartd-runner to root ... 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root produced unexpected output (102 bytes) to STDOUT/STDERR: 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: /etc/smartmontools/run.d/10mail: 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: /usr/lib/sendmail: No such file or directory Feb 21 09:14:03 Ubuntuserver smartd[8677]: . . . message not sent.]
Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root: successful

I'm missing a step (or steps) here, apparently. I've not changed the run.d/10mail and I don't have a /usr/lib/sendmail file or directory.

I'm a tad confused about the "-m root" specification in the DEVICESCAN lline. Is it "m root" or "m [email]email@address.com[/email]"

---

### Post by dcstar on 2013-02-21
> **mosscomes said:**
> I'm trying to configure an Ubuntu file server (12.04LTS) with smartmon tools to e-mail hard drive alerts. I'm using msmtp, on which I can receive test messages from the command line. When I try to send a test message via smartmon tools, it doesn't work. Thinking I needed one more piece in the mix, **I added heirloom mailx**, configured it and received a test mail. It still doesn't work when I try to send a test message through smartmon tools.

The syslog on this error keeps saying:

Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root: successful Feb 21 09:14:03 Ubuntuserver smartd[8677]: Executing test of /usr/share/smartmontools/smartd-runner to root ... 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root produced unexpected output (102 bytes) to STDOUT/STDERR: 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: /etc/smartmontools/run.d/10mail: 
Feb 21 09:14:03 Ubuntuserver smartd[8677]: /usr/lib/sendmail: No such file or directory Feb 21 09:14:03 Ubuntuserver smartd[8677]: . . . message not sent.]
Feb 21 09:14:03 Ubuntuserver smartd[8677]: Test of /usr/share/smartmontools/smartd-runner to root: successful

I'm missing a step (or steps) here, apparently. I've not changed the run.d/10mail and I don't have a /usr/lib/sendmail file or directory.

I'm a tad confused about the "-m root" specification in the DEVICESCAN lline. Is it "m root" or "m [email]email@address.com[/email]"

You need a mail user agent that supports the line format smartd uses, **bsd-mailx** works fine for me. You need an MTA that the user agent actually connects to, I use **postfix**.

You can redirect all e-mail sent to root by using /etc/aliases and rebuilding that database.

Add the "-M test" command after "-m root" to have it send a test email when you do the following to restart the service:

```
sudo dpkg-reconfigure smartmontools
```

---

