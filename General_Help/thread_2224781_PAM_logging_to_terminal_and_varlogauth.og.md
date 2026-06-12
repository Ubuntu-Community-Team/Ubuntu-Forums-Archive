---
title: "PAM logging to terminal and /var/log/auth.og"
date: 2014-05-18
forum: General Help
---

### Post by jaroon on 2014-05-18
Not sure what triggered this but within the last day or two my root terminal has been having PAM log messages written to my screen in addition to the log file:

```
grep 'May 18 01:42' /var/log/auth.log
May 18 01:42:00 arbitrium sshd[14043]: Failed password for root from 116.10.191.179 port 10013 ssh2
May 18 01:42:03 arbitrium sshd[14043]: Failed password for root from 116.10.191.179 port 10013 ssh2
May 18 01:42:06 arbitrium sshd[14043]: Failed password for root from 116.10.191.179 port 10013 ssh2
May 18 01:42:09 arbitrium sshd[14043]: Failed password for root from 116.10.191.179 port 10013 ssh2
May 18 01:42:11 arbitrium sshd[14043]: Failed password for root from 116.10.191.179 port 10013 ssh2
May 18 01:42:11 arbitrium sshd[14043]: Disconnecting: Too many authentication failures for root [preauth]
May 18 01:42:11 arbitrium sshd[14043]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.191.179  user=root
May 18 01:42:11 arbitrium sshd[14043]: PAM service(sshd) ignoring max retries; 6 > 3
```

With this line, and several others just like it, logged to my terminal:

```
May 18 01:42:11 arbitrium sshd[14043]: PAM service(sshd) ignoring max retries; 6 > 3
```

Just the normal brute forcing attempts that are always happening, but recently these log lines are being written to both the active root terminal and the log file. Any ideas on  PAM option I need to set, if this is a syslog thing or something completely else would be greatly appreciated.

Pretty annoying when they pop up in the middle of writing a long command or in the output of a report.

--Shields

---

