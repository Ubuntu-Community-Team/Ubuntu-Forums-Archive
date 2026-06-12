---
title: "Why logging to syslog file"
date: 2018-05-23
forum: General Help
---

### Post by sumegi-p on 2018-05-23
I am using Ubuntu 17.10.

It uses journald for logging and it stores the logs in /var/log/journal

Why there is a syslog file then?

---

### Post by Holger_Gehrke on 2018-05-23
First, by default, journald writes its logs to **/run/**log/journal/ and that's a ram disk (tmpfs) and will be gone after a crash - exactly the time when you need the information in them. On my XUbuntu 17.10 /var/log/journal doesn't exist, but the man page for systemd-journald states that if it existed, it would be used. Perhaps on main line Ubuntu somebody had the good idea to create that directory during installation. 
Second, the journals are binary and can only be read using journalctl or some other program that implements the same logic. After a serious crash you might end up with Ubuntu not booting. During analysis and recovery from such a crash you would need access to the logged information and not every emergency boot medium you might use is systemd based and has journalctl. I once - back in the stone age - used Windows XP in a dual boot setting with an ext2 driver to read the logs on my broken SuSE Linux - I don't think there's a windows port of journalctl, is there ?

Holger

---

