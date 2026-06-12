---
title: "&quot;No rules&quot; randomly launching Ubuntu 20.04LTS AWS images"
date: 2022-09-08
forum: General Help
---

### Post by alsparks on 2022-09-08
I build custom AMIs from Ubuntu base AMIs on EC2.  This has been successful until now.  Now I have random and sporadic failures launching an instance with auditd rules in place.  This has not been a problem until using current AMI and patches (us-west-2 region AMI [ami-0123376e204addb71]("https://console.aws.amazon.com/ec2/home?region=us-west-2#launchAmi=ami-0123376e204addb71")).

I am loading a CIS hardened rule set into auditd at boot.  Most instances I launch load the rules and successfully start auditd.  Occasionally, an instance will boot with auditctl -l output: "No rules," and systectl status of auditd is:

&#9679; auditd.service - Security Auditing Service
     Loaded: loaded (/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2022-09-06 19:26:48 UTC; 6min ago
       Docs: man:auditd(8)
             [https://github.com/linux-audit/audit-documentation](https://github.com/linux-audit/audit-documentation)
    Process: 337 ExecStart=/sbin/auditd (code=exited, status=1/FAILURE)

Sep 06 19:26:48 ip-10-208-228-78 auditd[363]: Started dispatcher: /sbin/audispd pid: 365
Sep 06 19:26:48 ip-10-208-228-78 auditd[363]: Error receiving audit netlink packet (No buffer space available)
Sep 06 19:26:48 ip-10-208-228-78 auditd[363]: Error setting audit daemon pid (No buffer space available)
Sep 06 19:26:48 ip-10-208-228-78 auditd[363]: Unable to set audit pid, exiting
Sep 06 19:26:48 ip-10-208-228-78 auditd[337]: Cannot daemonize (Success)
Sep 06 19:26:48 ip-10-208-228-78 auditd[337]: The audit daemon is exiting.
Sep 06 19:26:48 ip-10-208-228-78 auditd[363]: The audit daemon is exiting.
Sep 06 19:26:48 ip-10-208-228-78 systemd[1]: auditd.service: Control process exited, code=exited, status=1/FAILURE
Sep 06 19:26:48 ip-10-208-228-78 systemd[1]: auditd.service: Failed with result 'exit-code'.

When it fails, a reboot or just a restart of auditd service makes it work:

     Active: active (running) since Thu 2022-09-08 08:05:04 UTC; 54s ago
       Docs: man:auditd(8)
             [https://github.com/linux-audit/audit-documentation](https://github.com/linux-audit/audit-documentation)
    Process: 1638 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Process: 1643 ExecStartPost=/sbin/augenrules --load (code=exited, status=0/>
   Main PID: 1639 (auditd)
      Tasks: 2 (limit: 2309)
     Memory: 724.0K
     CGroup: /system.slice/auditd.service
             &#9492;&#9472;1639 /sbin/auditd

Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: backlog_wait_time 0
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: enabled 2
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: failure 1
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: pid 1639
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: rate_limit 0
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: backlog_limit 16384
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: lost 0
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: backlog 306
Sep 08 08:05:04 ip-10-210-197-43 augenrules[1673]: backlog_wait_time 0
Sep 08 08:05:04 ip-10-210-197-43 systemd[1]: Started Security Auditing Service.

I've never had to worry before about auditd randomly throwing a startup error.  I've tried everything I can think of to solve this, but I can't determine what the "(No buffer space available)" messages are telling me.  Cannot find any good solutions via Googling yet either.

I've tried:
* increasing the backlog size in the rules (-b 16384)
* also setting the size on the kernel boot line (audit=1 selinux=1 audit_backlog_limit=16384)
* removing all but a few rules I know are correct from the rules.d/audit.rules file
* saving an augenrules-created version of rules file as /etc/audit/audit.rules
* also changing /etc/default/auditd to USE_AUGENRULES="no"

In all cases, most instances launch with rules, but at least 1 in 5 launch with "No rules".  Same AMI, region, everything... except no loaded rules. Until a reboot, or auditd.service restart.

Does anyone understand what the service failure messages above mean, and what "buffer space" I'm out of?  The instances have 2GB RAM available, and were not a problem in the past.  I cannot see the same issue with Ubuntu 18 or 22, with same configurations.

These workarounds shouldn't be needed, but I can't figure out the inconsistency.  I'd appreciate any ideas to try or where to look for answers.  Thanks in advance.
-Alan

---

### Post by alsparks on 2022-09-08
I have an update on this - it appears to appear with a new kernel update.  When I backed up to an Ubuntu AMU5.15.0-1017-aws AMI dated 0810, the issue disappeared.  However, applying patches including the kernel caused this buffer issue and unreliable startup:

linux-aws/focal-updates,focal-security 5.15.0.1019.23~20.04.11 amd64 [upgradable from: 5.15.0.1017.21~20.04.9]
linux-headers-aws/focal-updates,focal-security 5.15.0.1019.23~20.04.11 amd64 [upgradable from: 5.15.0.1017.21~20.04.9]
linux-image-aws/focal-updates,focal-security 5.15.0.1019.23~20.04.11 amd64 [upgradable from: 5.15.0.1017.21~20.04.9]

I wonder if there is a bug posted for this.
-Alan

---

### Post by alsparks on 2022-09-13
I have another update on this, after a few days working though this.  The issue appears to depend on the kernel command line option "audit_backlog_limit".  I had originally set this as recommended by CIS guideline 4.1.1.4 to "audit_backlog_limit=8192".  This had worked fine until now.  Now, that option causes auditd to sometimes fail on boot with the above "Error receiving audit netlink packet (No buffer space available)" message,

I have tried increasing that from 8192 to 16384, and that offered no improvement.  Removing it, while in conflict to the CIS recommendations, resolves the intermittent failures.

Where do I report this issue?
-Alan

---

### Post by TheFu on 2022-09-13
> **alsparks said:**
>  Where do I report this issue?

To whoever created the AMI?  Google "report bugs AWS".  [https://aws.amazon.com/amazon-linux-ami/faqs/](https://aws.amazon.com/amazon-linux-ami/faqs/)

I've not seen this on any of my servers, but I don't use AWS images nor do I recognize that kernel option.

---

### Post by alsparks on 2022-09-13
I created the AMI.  I create AMIs of various Ubuntu flavors via Packer for company use.
And this code works for Ubuntu 18 and 22, and worked as far back as June  for Ubuntu 20 official images:  [https://cloud-images.ubuntu.com/locator/ec2/](https://cloud-images.ubuntu.com/locator/ec2/)

AWS is working this issue with me, but it isn't an Amazon image so this isn't exactly their bailiwick.
Thanks for the response though.

---

### Post by TheFu on 2022-09-13
You could open a bug with Canonical through launchpad. I suspect with paid support, it will get priority.
These forums are peer, volunteer, support. Nobody here works for Canonical.

---

### Post by alsparks on 2022-09-14
Thanks, I forgot Launchpad.  Will try that.

---

