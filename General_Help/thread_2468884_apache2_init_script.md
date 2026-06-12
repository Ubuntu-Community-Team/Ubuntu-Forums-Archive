---
title: "apache2 init script"
date: 2021-11-13
forum: General Help
---

### Post by Krischu on 2021-11-13
I had disabled my server's apache2 service some time ago and wanted to reactivate it again. The structure /etc/apache2 is stil there but I'm missing the /etc/init.d script.
Is there a simple command to restablish that script?

---

### Post by TheFu on 2021-11-13
Which release?
If systemd-based, did you mask the service _Unit_ file?  Just unmask it, then enable it using **systemctl**.  "It" being the service name.

---

### Post by Krischu on 2021-11-13
apache 2.4.29

What is the "service _Unit_" file and how does "It" refer to this? What would be the service name?

---

### Post by TheFu on 2021-11-13
Google found this searching for "systemd unit files" : [https://fedoramagazine.org/systemd-getting-a-grip-on-units/](https://fedoramagazine.org/systemd-getting-a-grip-on-units/)

Which _**OS**_ release?

---

