---
title: "Apparmor fails to start, gives cryptic error (ubuntu 18.04)"
date: 2019-10-05
forum: General Help
---

### Post by slhiro on 2019-10-05
Hi!
Always gives this error when I try to start it or at boot. No apparent reason... What should I look at?

```

~$ systemctl status apparmor.service 

&#9679; apparmor.service - AppArmor initialization
   Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2019-10-04 13:47:38; 1h 31min ago
     Docs: man:apparmor(7)
           http://wiki.apparmor.net/
  Process: 1387 ExecStart=/etc/init.d/apparmor start (code=exited, status=123)
 Main PID: 1387 (code=exited, status=123)

apparmor[1387]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
apparmor[1387]: Multiple definitions for hat sanitized_helper in profile (null) exist,bailing out.
apparmor[1387]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
apparmor[1387]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
apparmor[1387]: Multiple definitions for hat sanitized_helper in profile (null) exist,bailing out.
apparmor[1387]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
apparmor[1387]:    ...fail!
systemd[1]: apparmor.service: Main process exited, code=exited, status=123/n/a
systemd[1]: apparmor.service: Failed with result 'exit-code'.
systemd[1]: Failed to start AppArmor initialization.
```

---

### Post by #&amp;thj^% on 2019-10-05
It can be solved installing apparmor-easyprof-ubuntu or creating the folders by hand. 
```
sudo apt install apparmor-easyprof-ubuntu
```
Old bug keeps creeping in: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1554803](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1554803)

---

### Post by slhiro on 2019-10-05
[B]1fallen
[/B]Thanks for looking, but it's not it. Stil the same error.
The bug you referenced had 'AppArmor parser error' in logs. I don't have those.

> $ sudo apt install apparmor-easyprof 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apparmor-easyprof is already the newest version (2.12-4ubuntu5.1).
0 upgraded, 0 newly installed, 0 to remove and 188 not upgraded.

$ sudo apt install --reinstall apparmor-easyprof 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 188 not upgraded.
Need to get 10,3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 apparmor-easyprof all 2.12-4ubuntu5.1 [10,3 kB]
Fetched 10,3 kB in 6s (1&#8239;877 B/s)              
(Reading database ... 247948 files and directories currently installed.)
Preparing to unpack .../apparmor-easyprof_2.12-4ubuntu5.1_all.deb ...
Unpacking apparmor-easyprof (2.12-4ubuntu5.1) over (2.12-4ubuntu5.1) ...
Setting up apparmor-easyprof (2.12-4ubuntu5.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...

$ sudo systemctl start apparmor

---

