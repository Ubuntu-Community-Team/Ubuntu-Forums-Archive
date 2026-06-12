---
title: "syslog not updating after upgrade to 15.04"
date: 2015-05-14
forum: General Help
---

### Post by odror on 2015-05-14
Hi

After upgrading to 15.04. /var/log/syslog is en empty file. it is not updating. Is this a setup issue or systemd/15.04 issue.

Is it now in a new location ? (like many ubuntu users I am very new to systemd)

ls -ls syslog:
> 0 -rw-r----- 1 syslog adm 0 May 13 10:41 syslog


---

### Post by PhilGil on 2015-05-14
I can't confirm as I'm not at my 15.04 system right now, but I do believe the missing syslog file is due to systemd. The systemd equivalent is journalctl. Lots of good information on the systemd journal (including a method for writing the journal to syslog) in the [Arch Wiki]("https://wiki.archlinux.org/index.php/Systemd"). Scroll down to the "journal" section of the web page.

---

### Post by odror on 2015-05-14
Thanks that was the issue.

---

