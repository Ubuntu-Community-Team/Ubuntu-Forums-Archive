---
title: "ubuntu 15.10 freezes after latest updates"
date: 2016-07-16
forum: General Help
---

### Post by Pitero on 2016-07-16
Hi,

I have ubuntu 15.10 and lately installed few updates. Unfortunately after this ubuntu freezes from time to time. Until now it always happened when browsing Internet in Firefox. I can still move cursor but I'm not able to run any new application from Ubuntu menu. When clicking Cltr+Alt+F1 I'm able to switch to terminal but after entering user name, the system is halted here also and is not asking for password. However if I log in to terminal previously I can still ex. list all processes. Unfortunately killing firefox is usually not possible. Firefox process is still active even after killing it as kill -9. Usually after some time ex. 15-30 seconds system start to work normally (whatever I kill or not kill firefox) (but not always).

As I'm not too advanced user, thus I would need quite clear clarification what to do/what to check. I've tried to run older kelner but pressing Shift doesn't work when rebooting (system starts normally, there is no menu, perhaps it's related with that I use UEFI).

Please have also a look on updates which were installed lately.

```
Commandline: aptdaemon role='role-commit-packages' sender=':1.95'
Install: linux-image-extra-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic), linux-image-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic), linux-headers-4.2.0-42:amd64 (4.2.0-42.49, automatic), linux-headers-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic), linux-signed-image-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic)
Upgrade: linux-headers-generic:amd64 (4.2.0.41.44, 4.2.0.42.45), dkms:amd64 (2.2.0.3-2ubuntu6.1, 2.2.0.3-2ubuntu6.2), libarchive13:amd64 (3.1.2-11ubuntu0.15.10.1, 3.1.2-11ubuntu0.15.10.2), dh-python:amd64 (2.20150826ubuntu1, 2.20150826ubuntu1.1), libecryptfs1:amd64 (108-0ubuntu1.1, 108-0ubuntu1.2), linux-signed-generic:amd64 (4.2.0.41.44, 4.2.0.42.45), ecryptfs-utils:amd64 (108-0ubuntu1.1, 108-0ubuntu1.2), linux-signed-image-generic:amd64 (4.2.0.41.44, 4.2.0.42.45), linux-libc-dev:amd64 (4.2.0-41.48, 4.2.0-42.49), linux-image-generic:amd64 (4.2.0.41.44, 4.2.0.42.45), linux-generic:amd64 (4.2.0.41.44, 4.2.0.42.45)


Commandline: aptdaemon role='role-commit-packages' sender=':1.97'
Install: mokutil:amd64 (0.3.0-0ubuntu3~15.10.1, automatic)
Upgrade: shim-signed:amd64 (1.11+0.8-0ubuntu2, 1.17~15.10.1+0.8-0ubuntu2)


Commandline: aptdaemon role='role-commit-packages' sender=':1.103'
Install: libept1.4.16:amd64 (1.0.14ubuntu1.1, automatic), rarian-compat:amd64 (0.8.1-6, automatic), libvte-2.90-9:amd64 (0.36.3-1ubuntu2, automatic), libvte-2.90-common:amd64 (0.36.3-1ubuntu2, automatic), sgml-data:amd64 (2.0.10, automatic), docbook-xml:amd64 (4.5-7.3, automatic), librarian0:amd64 (0.8.1-6, automatic), synaptic:amd64 (0.81.4build2)
```

---

### Post by slickymaster on 2016-07-16
*Moved to the ***General Help*** sub-forum*

---

### Post by jeremy31 on 2016-07-16
It should be time to upgrade to Ubuntu 16.04 as 15.10 will be EOL in a short time, likely by the end of July the update servers will be offline

---

### Post by Pitero on 2016-07-17
Unfortunately I can't upgrade to 16.04 as my computer is not properly supported. There was some issue with i7 skylyke and two graphic cards when there is display port and hdmi in laptop. It was promised to be solved in the next version.

Concluding do you have any ideas what to check/how to solve my problem?

I've checked /var/log/syslog in the moment when computer freezes but there is nothing suspicious then (there are other red entries but first they don't look to suspicious, secondly there is the difference ex. 20 minutes of time.

---

