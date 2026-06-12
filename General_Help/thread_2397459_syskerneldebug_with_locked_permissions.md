---
title: "/sys/kernel/debug with locked permissions"
date: 2018-07-29
forum: General Help
---

### Post by ozp on 2018-07-29
I'm tying to use Hybrid Graphics and there is a step that I can't do:

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

It says

```
cat: /sys/kernel/debug/vgaswitcheroo/switch: Operation not permitted
```


I've found that the /sys/kernel/debug directory have a wierd permission. Even with root I cannot change anything there.  If I change the permission , I still cannot change anything 

Maybe it is related to "debugfs" that will change permissions back every reboot.

---

### Post by ozp on 2018-07-31
```
 

Job for switcheroo-control.service failed because the control process exited with error code.
See "systemctl status switcheroo-control.service" and "journalctl -xe" for details.

ozp@ozp-Inspiron-7520:~$ systemctl status switcheroo-control.service

&#9679; switcheroo-control.service - Switcheroo Control Proxy service
   Loaded: loaded (/lib/systemd/system/switcheroo-control.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-07-31 22:35:28 -03; 19s ago
  Process: 4529 ExecStart=/usr/sbin/switcheroo-control (code=exited, status=1/FAILURE)
 Main PID: 4529 (code=exited, status=1/FAILURE)

jul 31 22:35:28 ozp-Inspiron-7520 systemd[1]: Starting Switcheroo Control Proxy service...
jul 31 22:35:28 ozp-Inspiron-7520 switcheroo-cont[4529]: switcheroo-control could not query vga_switcheroo status: Operation not permitted
jul 31 22:35:28 ozp-Inspiron-7520 systemd[1]: switcheroo-control.service: Main process exited, code=exited, status=1/FAILURE
jul 31 22:35:28 ozp-Inspiron-7520 systemd[1]: switcheroo-control.service: Failed with result 'exit-code'.
jul 31 22:35:28 ozp-Inspiron-7520 systemd[1]: Failed to start Switcheroo Control Proxy service.

ozp@ozp-Inspiron-7520:~$ 
``` 

Also the switcheroo has problems 

This is very awkward

---

### Post by camelopardalis2 on 2019-02-28
For anybody having the same problem; I've found a solution:

Disable 'Secure boot' in the BIOS and that let's you access the /sys/kernel/debug properly.
[https://bugs.launchpad.net/ubuntu/+source/switcheroo-control/+bug/1768988](https://bugs.launchpad.net/ubuntu/+source/switcheroo-control/+bug/1768988)

---

