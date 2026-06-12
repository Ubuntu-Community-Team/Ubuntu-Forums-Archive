---
title: "ACPI Error"
date: 2019-09-10
forum: General Help
---

### Post by kbocek2 on 2019-09-10
Working on a new install of Server 18.04.3 on a headless server. Attempts to start acpid fail. This was suggested:

```
dpkg --configure -a

```
But that throws an error:

```
Setting up acpid (1:2.0.28-1ubuntu1) ...
Job for acpid.service failed because of unavailable resources or another system error.
See "systemctl status acpid.service" and "journalctl -xe" for details.
invoke-rc.d: initscript acpid, action "start" failed.
&#9679; acpid.service - ACPI event daemon
   Loaded: loaded (/lib/systemd/system/acpid.service; disabled; vendor preset: enabled)
   Active: failed (Result: resources)

Sep 10 08:59:37 myth systemd[1]: acpid.service: Failed with result 'resources'.
Sep 10 08:59:37 myth systemd[1]: Failed to start ACPI event daemon.
Sep 10 08:59:38 myth systemd[1]: acpid.service: Got no socket.
Sep 10 08:59:38 myth systemd[1]: acpid.service: Failed to run 'start' task: Invalid argument
Sep 10 08:59:38 myth systemd[1]: acpid.service: Failed with result 'resources'.
Sep 10 08:59:38 myth systemd[1]: Failed to start ACPI event daemon.
Sep 10 08:59:38 myth systemd[1]: acpid.service: Got no socket.
Sep 10 08:59:38 myth systemd[1]: acpid.service: Failed to run 'start' task: Invalid argument
Sep 10 08:59:38 myth systemd[1]: acpid.service: Failed with result 'resources'.
Sep 10 08:59:38 myth systemd[1]: Failed to start ACPI event daemon.
dpkg: error processing package acpid (--configure):
 installed acpid package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.

dpkg: error processing package acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support


```

Does anyone have any idea what's going on? There doesn't seem to be a package named acpi-support.

---

### Post by Xian on 2019-09-11
First let's stop the service acpid:

```
sudo /etc/init.d/acpid stop
```

After stopped use dpkg to configure the application:

```
sudo dpkg --configure -a
```

Then restart the service:

```
sudo /etc/init.d/acpid start
```

---

### Post by kbocek2 on 2019-09-14
I'm sure I tried [FONT=courier new]systemctl stop acpid[/FONT]. However after a power outage the host isn't coming back up. I have to say, my experience with Ubuntu, both server and desktop, has not been smooth. Lots of little problems on both.

---

