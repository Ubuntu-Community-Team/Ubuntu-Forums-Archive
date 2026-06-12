---
title: "org.gnome.nautilus repeating error making log files too large"
date: 2021-02-02
forum: General Help
---

### Post by biglittlebot on 2021-02-02
Hello, I'm currently receiving this repeating error in my logfiles > Feb  1 14:34:58 bot-XPS-13-9343 org.gnome.Nautilus[32700]: Type 1 or 2, then press enter. Feb  1 14:34:58 bot-XPS-13-9343 org.gnome.Nautilus[32700]: That's not a valid option.   And it has made syslog 35 Gigabytes and syslog.1 145 Gigabytes which is the rest of my storage space, which also makes them too large to delete with logrotate, it's reporting they're too large to be log files so wont force a rotate or outright delete them.   I am new to linux, so i'm unsure of what commands to use to provide additional data and have been unable to find a solution elsewhere. So any help fixing the repeating error and help with deleting the log files would be appreciated.

---

