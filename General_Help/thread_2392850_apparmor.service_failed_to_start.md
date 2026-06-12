---
title: "apparmor.service failed to start"
date: 2018-05-26
forum: General Help
---

### Post by kazakore on 2018-05-26
To me it looks like it doesn't like the removal of snapd. No I'm not willing to add snap back to the system!

From [This Bug](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1554803) it looks like there is a package to add directories to fix this failing when a directory isn't found, I can only assume the apparmor-easyprof package in 18.04 is the replacement for apparmor-easyprof-ubuntu in 17.10 but installing it does not fix the issue!

Is apparmor really needed? Is the way it handles permissions needed by any programs? Is it more secure than whatever fallback method I assume I must be using? There doesn't seem to be a huge amount of information on the web....

```
$ sudo systemctl status apparmor
&#9679; apparmor.service - AppArmor initialization
   Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2018-05-26 10:36:35 BST; 38s ago
     Docs: man:apparmor(7)
           http://wiki.apparmor.net/
  Process: 2850 ExecStart=/etc/init.d/apparmor start (code=exited, status=123)
 Main PID: 2850 (code=exited, status=123)

May 26 10:36:35 ThisOne apparmor[2850]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
May 26 10:36:35 ThisOne apparmor[2850]: AppArmor parser error for /etc/apparmor.d/usr.lib.snapd.snap-confine.real in /etc/apparmor.d/usr.lib.snapd.snap-confine.real at line 11: Could not open '/var/lib/snapd/apparmor/snap-confine'
May 26 10:36:35 ThisOne apparmor[2850]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
May 26 10:36:35 ThisOne apparmor[2850]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
May 26 10:36:35 ThisOne apparmor[2850]: AppArmor parser error for /etc/apparmor.d/usr.lib.snapd.snap-confine.real in /etc/apparmor.d/usr.lib.snapd.snap-confine.real at line 11: Could not open '/var/lib/snapd/apparmor/snap-confine'
May 26 10:36:35 ThisOne apparmor[2850]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
May 26 10:36:35 ThisOne apparmor[2850]:    ...fail!
May 26 10:36:35 ThisOne systemd[1]: apparmor.service: Main process exited, code=exited, status=123/n/a
May 26 10:36:35 ThisOne systemd[1]: apparmor.service: Failed with result 'exit-code'.
May 26 10:36:35 ThisOne systemd[1]: Failed to start AppArmor initialization.

$ sudo apt-get install apparmor-easyprof 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apparmor-easyprof is already the newest version (2.12-4ubuntu5).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

$ sudo systemctl start apparmor.service
Job for apparmor.service failed because the control process exited with error code.
See "systemctl status apparmor.service" and "journalctl -xe" for details.

```

---

### Post by kazakore on 2018-05-26
OK I did:

```
$ find  /etc/apparmor.d/ -iname "*snap*"
/etc/apparmor.d/usr.lib.snapd.snap-confine.real
/etc/apparmor.d/cache/usr.lib.snapd.snap-confine.real
/etc/apparmor.d/local/usr.lib.snapd.snap-confine.real
```

then moved those three files into a backup location in Home, just in case. Now apparmor starts. Still seems a rather buggy bit of software if it wont even start if software it once managed is removed!!! Plus I would still like to know how much difference it makes....

---

