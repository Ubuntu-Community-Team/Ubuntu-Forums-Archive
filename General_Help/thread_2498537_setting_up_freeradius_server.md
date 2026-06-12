---
title: "setting up freeradius server"
date: 2024-06-18
forum: General Help
---

### Post by rrmcguire on 2024-06-18
Hello I'm very new using ubuntu and am trying to setup a freeradius server using ubuntu 22.04. I have run through almost the entire process here:

[https://docs.beamnetworks.dev/en/linux/networking/freeradius-install](https://docs.beamnetworks.dev/en/linux/networking/freeradius-install)

But when I get to the point of writing sudo systemctl restart freeradius 


I receive the following below, any help would be appreciated

Job for freeradius.service failed because the control process exited with error code.
See "systemctl status freeradius.service" and "journalctl -xeu freeradius.service" for details.



freeradius.service - FreeRADIUS multi-protocol policy server
     Loaded: loaded (/lib/systemd/system/freeradius.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: exit-code) since Tue 2024-06-18 16:07:52 UTC; 5s ago
       Docs: man:radiusd(8)
             man:radiusd.conf(5)
             [http://wiki.freeradius.org/](http://wiki.freeradius.org/)
             [http://networkradius.com/doc/](http://networkradius.com/doc/)
    Process: 53907 ExecStartPre=/usr/sbin/freeradius $FREERADIUS_OPTIONS -Cx -lstdout (code=exited, status=1/FAILURE)
        CPU: 123ms

Jun 18 16:07:52 freeradius systemd[1]: freeradius.service: Control process exited, code=exited, status=1/FAILURE
Jun 18 16:07:52 freeradius systemd[1]: freeradius.service: Failed with result 'exit-code'.
Jun 18 16:07:52 freeradius systemd[1]: Failed to start FreeRADIUS multi-protocol policy server.
Jun 18 16:07:57 freeradius systemd[1]: freeradius.service: Scheduled restart job, restart counter is at 89.
Jun 18 16:07:57 freeradius systemd[1]: Stopped FreeRADIUS multi-protocol policy server.
Jun 18 16:07:57 freeradius systemd[1]: Starting FreeRADIUS multi-protocol policy server...

---

### Post by currentshaft on 2024-06-18
It's right in your output:

/usr/sbin/freeradius $FREERADIUS_OPTIONS -Cx -lstdout

This command failed. Try running it without systemctl to figure out why, possibly due to an error in your config.

---

