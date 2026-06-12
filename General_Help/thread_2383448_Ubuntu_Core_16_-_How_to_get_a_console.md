---
title: "Ubuntu Core 16 - How to get a console?"
date: 2018-01-25
forum: General Help
---

### Post by fad0 on 2018-01-25
My first post.  The seems to be the most appropriate place to post this question.

Setup: Ubuntu Core 16 running on RaspberryPi3, ssh'ing from MacAir.

I can ssh username@myip and get a terminal.  But I would like to see system messages (console messages) which would normally be written to a console terminal.  For security, I have set "PasswordAuthentication no" in my sshd_config file, so I don't think I can ssh as "root" (I tried unsuccessfully).

Is there a way to invoke a console terminal so I can monitor console messages?

-fad0

---

### Post by TheFu on 2018-01-25
Welcome to the forums.

By definition, an ssh connection is NOT a console.  Console messages are written out the HDMI port on r-pis, so connect up an HDMI screen to see them and prevent any graphical programs from running.

Or you can look at the logs under /var/log/* ... syslog, dmesg are usually the main ones.  Use tail -f.

Remote root should never be allowed. Huge security issue, even on a LAN-only connection.

---

### Post by fad0 on 2018-01-25
Thanks TheFu.  Ubuntu Core only displays the host key fingerprints and the ssh username@ipaddress when directly connected to the RPi3 HDMI.  So console information does not get displayed there.

I will monitor the logs.  Thanks.

---

