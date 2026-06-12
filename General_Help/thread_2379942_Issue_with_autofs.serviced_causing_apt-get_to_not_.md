---
title: "Issue with autofs.serviced causing apt-get to not run"
date: 2017-12-11
forum: General Help
---

### Post by drakal30 on 2017-12-11
```
Linux mordor 4.10.0-37-generic #41-Ubuntu SMP Fri Oct 6 20:20:37 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
Here is the following error when trying to update or install new packages via apt-get.
```
root@mordor:/# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up autofs (5.1.2-1ubuntu1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Job for autofs.service failed because the control process exited with error code.
See "systemctl status autofs.service" and "journalctl -xe" for details.
invoke-rc.d: initscript autofs, action "start" failed.
&#9679; autofs.service - Automounts filesystems on demand
   Loaded: loaded (/lib/systemd/system/autofs.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-12-11 12:51:20 EST; 6ms ago
  Process: 32065 ExecStart=/usr/sbin/automount $OPTIONS --pid-file /var/run/autofs.pid (code=exited, status=1/FAILURE)
      CPU: 4ms

Dec 11 12:51:20 mordor systemd[1]: Starting Automounts filesystems on demand...
Dec 11 12:51:20 mordor automount[32065]: /usr/sbin/automount: test mount forbidden or incorrect kernel protocol version, kernel protocol version 5.00 or above required.
Dec 11 12:51:20 mordor systemd[1]: autofs.service: Control process exited, code=exited status=1
Dec 11 12:51:20 mordor systemd[1]: Failed to start Automounts filesystems on demand.
Dec 11 12:51:20 mordor systemd[1]: autofs.service: Unit entered failed state.
Dec 11 12:51:20 mordor systemd[1]: autofs.service: Failed with result 'exit-code'.
dpkg: error processing package autofs (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 autofs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Also this.
```
root@mordor:/# journalctl -u autofs
-- Logs begin at Sun 2017-12-10 20:11:56 EST, end at Mon 2017-12-11 12:50:05 EST. --
Dec 10 20:12:10 mordor systemd[1]: Starting Automounts filesystems on demand...
Dec 10 20:12:10 mordor automount[1744]: /usr/sbin/automount: test mount forbidden or incorrect kernel protocol version, kernel protocol version 5.00 or above required.
Dec 10 20:12:10 mordor systemd[1]: autofs.service: Control process exited, code=exited status=1
Dec 10 20:12:10 mordor systemd[1]: Failed to start Automounts filesystems on demand.
Dec 10 20:12:10 mordor systemd[1]: autofs.service: Unit entered failed state.
Dec 10 20:12:10 mordor systemd[1]: autofs.service: Failed with result 'exit-code'.
Dec 10 20:12:54 mordor systemd[1]: Starting Automounts filesystems on demand...
Dec 10 20:12:54 mordor automount[3072]: /usr/sbin/automount: test mount forbidden or incorrect kernel protocol version, kernel protocol version 5.00 or above required.
Dec 10 20:12:54 mordor systemd[1]: autofs.service: Control process exited, code=exited status=1
Dec 10 20:12:54 mordor systemd[1]: Failed to start Automounts filesystems on demand.
Dec 10 20:12:54 mordor systemd[1]: autofs.service: Unit entered failed state.
Dec 10 20:12:54 mordor systemd[1]: autofs.service: Failed with result 'exit-code'.
Dec 10 20:13:11 mordor systemd[1]: Starting Automounts filesystems on demand...
```

Thanks for the help.

---

### Post by drakal30 on 2017-12-12
I tried removing the package again via apt-get remove and it worked.   Not sure why it didn't work the last few times I tried.

---

