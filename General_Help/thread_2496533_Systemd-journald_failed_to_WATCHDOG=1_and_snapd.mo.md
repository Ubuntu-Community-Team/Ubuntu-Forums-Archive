---
title: "Systemd-journald failed to WATCHDOG=1 and snapd.mounts.target: failed to activate"
date: 2024-04-02
forum: General Help
---

### Post by MarcoPau on 2024-04-02
Hi there, I am getting a couple of errors and can't go further with apt full-upgrade. 

Snapd.mounts.target failed to activate service org.freedesktop.systemd1 

I searched the forum and wanted to

systemctl status org.freedesktop.systemd1

But I have no systemd nor systemctl installed and can't installa them since dpkg is stuck with the upgrade. Can I maybe skip the dpkg - -configure -a request in order to install systemctl and check the log?

Any other hint?

Thanks a bunch!

---

### Post by MarcoPau on 2024-04-02
Managed to kill apt and dpkg but systemctl status goes again to

Systemd-journald failed to send WATCHDOG=1 notification message: transport endpoint is not connected

Hope I can get out of this mess...!

---

### Post by Rubi1200 on 2024-04-02
What distro do you have installed and which version?

---

### Post by MarcoPau on 2024-04-02
I am running Kubuntu Mantic. Actually I don't use KDE but I use LXQt.

Thanks!

---

### Post by MarcoPau on 2024-04-02
I am back on the computer and tried being a bit more patient. Seems like things get thru if I wait long, but most of the tasks like apt update and others always give this time out error:

Failed to start "name of service": failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
See system logs and 'systemctl status "name of service"' for details

Hope this helps!

---

### Post by Rubi1200 on 2024-04-02
Is KDE still installed or you completely switched to LXQt?

I am wondering what the source of these issues might be and whether changing DE at login could help?

---

