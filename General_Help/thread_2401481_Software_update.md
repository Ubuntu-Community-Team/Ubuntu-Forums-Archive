---
title: "Software update"
date: 2018-09-18
forum: General Help
---

### Post by jbcohen on 2018-09-18
My system is set to update automatically, can umbuntu show me when it updated, what it updated?

---

### Post by Dennis N on 2018-09-18
Yes. Updated packages are logged in files in **/var/log/apt**. The most recent file is **history.log**, and older logs are stored as archive files like **history.log.1.gz**

Entries in history.log. First transaction is probably standard upgrade (user oks first), second is an unattended upgrade. 
```
Start-Date: 2018-09-17  07:40:00
Commandline: aptdaemon role='role-commit-packages' sender=':1.108'
Upgrade: firefox-locale-en:amd64 (62.0+build2-0ubuntu0.18.04.4, 62.0+build2-0ubuntu0.18.04.5), firefox:amd64 (62.0+build2-0ubuntu0.18.04.4, 62.0+build2-0ubuntu0.18.04.5), libcurl3-gnutls:amd64 (7.58.0-2ubuntu3.2, 7.58.0-2ubuntu3.3)
End-Date: 2018-09-17  07:40:11

Start-Date: 2018-09-19  08:09:18
Commandline: /usr/bin/unattended-upgrade
Upgrade: libglib2.0-bin:amd64 (2.56.2-0ubuntu0.18.04.1, 2.56.2-0ubuntu0.18.04.2), libglib2.0-0:amd64 (2.56.2-0ubuntu0.18.04.1, 2.56.2-0ubuntu0.18.04.2)
End-Date: 2018-09-19  08:09:23

```

---

