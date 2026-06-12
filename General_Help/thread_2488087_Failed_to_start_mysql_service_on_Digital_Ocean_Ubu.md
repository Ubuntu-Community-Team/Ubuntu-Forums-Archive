---
title: "Failed to start mysql service on Digital Ocean Ubuntu 22.04."
date: 2023-06-22
forum: General Help
---

### Post by jiapei100 on 2023-06-22
```console
&#8906;> ~ uname -a                                                                                                                                                                                                                                                                15:09:51
Linux localhost 5.15.0-75-generic #82-Ubuntu SMP Tue Jun 6 23:10:23 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
&#8906;> ~ lsb_release -a                                                                                                                                                                                                                                                          15:09:52
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy
&#8906;> ~ sudo service mysqld restart                                                                                                                                                                                                                                             15:09:57
Failed to restart mysqld.service: Unit mysqld.service not found.
&#8906;> ~ sudo service mysql restart                                                                                                                                                                                                                                              15:10:07
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xeu mysql.service" for details.
&#8906;> ~ sudo service mysql status                                                                                                                                                                                                                                               15:10:10
× mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2023-06-22 15:10:12 PDT; 3s ago
    Process: 13475 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)
        CPU: 11ms

Jun 22 15:10:12 localhost systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Jun 22 15:10:12 localhost systemd[1]: Stopped MySQL Community Server.
Jun 22 15:10:12 localhost systemd[1]: mysql.service: Start request repeated too quickly.
Jun 22 15:10:12 localhost systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 22 15:10:12 localhost systemd[1]: Failed to start MySQL Community Server.
```


Can anybody please give me a hand?

Cheers

---

### Post by jiapei100 on 2023-06-23
Problem solved finally by removing ALL MySQL related packages and folders...

---

### Post by ActionParsnip on 2023-06-23
Please mark as solved.

If you want a SQL server, Digital Ocean do serverless SQL and you get a DB without caring about the OS layer

---

