---
title: "failed to start LSB: AppArmor initialisation"
date: 2017-03-21
forum: General Help
---

### Post by glatt on 2017-03-21
Hi! While starting Ubuntu 16.04 LTS above message is displayed.
A closer look shows that apparmor and profiles are loaded, however this seems to contradict the missing initialization.
I guess apparmor should be enabled. But how? Thanks for advice!

PC:~$ systemctl status apparmor.service
&#9679; apparmor.service - LSB: AppArmor initialization
   Loaded: loaded (/etc/init.d/apparmor; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Die 2017-03-21 10:17:36 CET; 52s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2875 ExecStart=/etc/init.d/apparmor start (code=exited, status=123)

Mär 21 10:17:36 PC apparmor[2875]: AppArmor parser error for /etc/apparmor.d/usr
Mär 21 10:17:36 PC apparmor[2875]: Skipping profile in /etc/apparmor.d/disable: 
Mär 21 10:17:36 PC apparmor[2875]: Skipping profile in /etc/apparmor.d/disable: 
Mär 21 10:17:36 PC apparmor[2875]: AppArmor parser error for /etc/apparmor.d/usr
Mär 21 10:17:36 PC apparmor[2875]: Skipping profile in /etc/apparmor.d/disable: 
Mär 21 10:17:36 PC apparmor[2875]:    ...fail!
Mär 21 10:17:36 PC systemd[1]: apparmor.service: Control process exited, code=ex
Mär 21 10:17:36 PC systemd[1]: Failed to start LSB: AppArmor initialization.
Mär 21 10:17:36 PC systemd[1]: apparmor.service: Unit entered failed state.
Mär 21 10:17:36 PC systemd[1]: apparmor.service: Failed with result 'exit-code'.

and:

PC:~$ sudo aa-status
apparmor module is loaded.
21 profiles are loaded.PC:~$ sudo aa-status
apparmor module is loaded.
21 profiles are loaded.
21 profiles are in enforce mode.
 etc.

---

