---
title: "Accountservice/GDM Issue"
date: 2022-01-23
forum: General Help
---

### Post by giobaxx on 2022-01-23
Hello GUys


I need an help to understand an help about how to fix an issue with the accountsservice which goes in timeout preventing ubuntuù
to boot properly. Basically gdm does not start because of that. This is bascally the error:

> 
Jan 05 17:21:21 client01 dbus-daemon[1428]: [system] Activating via systemd: service name='org.freedesktop.Accounts' unit='accounts-daemon.service' requested by ':1.2474505' (uid=0 pid=8551 comm="/usr/sbin/gdm3 " label="unconfined")
Jan 05 17:05:07 client01 dbus-daemon[1428]: [system] Failed to activate service 'org.freedesktop.Accounts': timed out (service_start_timeout=25000ms)
Jan 05 17:05:07 client01 gdm3[7666]: Failed to contact accountsservice: Error calling StartServiceByName for org.freedesktop.Accounts: GDBus.Error:org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.freedesktop.Accounts': timed out (service_start_timeout=25000ms)
Jan 05 17:05:07 client01 systemd[1]: gdm.service: Main process exited, code=exited, status=1/FAILURE
Jan 05 17:05:07 client01 systemd[1]: gdm.service: Failed with result 'exit-code'.
Jan 05 17:05:08 client01 systemd[1]: gdm.service: Service hold-off time over, scheduling restart.
Jan 05 17:05:08 client01 systemd[1]: gdm.service: Scheduled restart job, restart counter is at 38.
Jan 05 17:05:08 client01 systemd[1]: Stopped GNOME Display Manager.
Jan 05 17:05:08 client01 systemd[1]: Starting Detect the available GPUs and deal with any system changes...
Jan 05 17:05:08 client01 systemd[1]: Started Detect the available GPUs and deal with any system changes.
Jan 05 17:05:08 client01 systemd[1]: Starting GNOME Display Manager...
Jan 05 17:05:08 client01 systemd[1]: Started GNOME Display Manager.
Jan 05 17:05:08 client01 dbus-daemon[1428]: [system] Activating via systemd: service name='org.freedesktop.Accounts' unit='accounts-daemon.service' requested by ':1.2297289' (uid=0 pid=7886 comm="/usr/sbin/gdm3 " label="unconfined")
Jan 05 17:05:33 client01 dbus-daemon[1428]: [system] Failed to activate service 'org.freedesktop.Accounts': timed out (service_start_timeout=25000ms)
Jan 05 17:05:33 client01 gdm3[7886]: Failed to contact accountsservice: Error calling StartServiceByName for org.freedesktop.Accounts: GDBus.Error:org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.freedesktop.Accounts': timed out (service_start_timeout=25000ms)


 


 
I've tried to unistall/reinstall the accountsservice package, reinstall gdm, but nothing worked. i'm to see the account-daemon take al loot of CPU cicle with dbus-daemon. but i really don't know what i can try to fix it, any adivce?

Al.

---

