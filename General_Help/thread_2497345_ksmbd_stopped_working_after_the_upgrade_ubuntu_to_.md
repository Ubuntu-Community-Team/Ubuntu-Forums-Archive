---
title: "ksmbd stopped working after the upgrade ubuntu to 24.04"
date: 2024-05-01
forum: General Help
---

### Post by bern1 on 2024-05-01
[COLOR=#000000][COLOR=#000000]Hello,[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]I've just upgraded Ubuntu to 24.04 (from 23.10).
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]Unfortunately ksmbd service has stopped working.[/COLOR][/COLOR]
[COLOR=#000000]When I try to install 'ksmbd-tools'. I receive an error:
[/COLOR]```
el@akacja:~$ sudo apt-get install ksmbd-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  ksmbd-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/68.2 kB of archives.
After this operation, 190 kB of additional disk space will be used.
(Reading database ... 243832 files and directories currently installed.)
Preparing to unpack .../ksmbd-tools_3.5.1-1build2_amd64.deb ...
Unpacking ksmbd-tools (3.5.1-1build2) ...
dpkg: error processing archive /var/cache/apt/archives/ksmbd-tools_3.5.1-1build2_amd64.deb (--unpack):
 unable to open '/usr/lib/systemd/system/ksmbd.service.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
       Errors were encountered while processing:
 /var/cache/apt/archives/ksmbd-tools_3.5.1-1build2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What to do to move on?
[COLOR=#000000][COLOR=#000000]
[/COLOR][/COLOR]

---

### Post by dimitriskarv on 2024-05-19
I have the exactlysame problem, after upgrade to kubuntu 24.04, log says:  *Error while installing package: unable to open '/usr/lib/systemd/system/ksmbd.service.dpkg-new  *
I was wandering if to uninstall smb, but I saw this in forum.

---

### Post by Morbius1 on 2024-05-19
It's a bug: [https://bugs.launchpad.net/ubuntu/+source/ksmbd-tools/+bug/2064694](https://bugs.launchpad.net/ubuntu/+source/ksmbd-tools/+bug/2064694)

Looks like a packaging issue to me but note that it is labeled "Fix Committed"

---

