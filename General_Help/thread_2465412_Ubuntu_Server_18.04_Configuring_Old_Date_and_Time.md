---
title: "Ubuntu Server 18.04 Configuring Old Date and Time"
date: 2021-08-01
forum: General Help
---

### Post by ohadr on 2021-08-01
Hi All,
I've a Ubuntu 18.04 server, I'm trying to set the server with a date older than 2018 but after a reboot the server reverts back to to a specific date and time (January 28 2018).
I've tried the below actions:

Disable all clock sync from internal services and from the hypervisor host
Synced it with an NTP server that has an older date

If I set the date after Jan 28 2018 the server does not revert back time date.

Has anyone else experienced this behavior? Any suggestions what can cause this?

Thanks,

Ohad.

---

### Post by him610 on 2021-08-01
Maybe January 28 2018 was the date of manufacture for your chip set.

---

