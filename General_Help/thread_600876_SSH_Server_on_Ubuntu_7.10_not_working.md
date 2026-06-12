---
title: "SSH Server on Ubuntu 7.10 not working"
date: 2007-11-02
forum: General Help
---

### Post by trymbill on 2007-11-02
I just installed Ubuntu 7.10 from scratch on my server.  I had been working with an old version of Ubuntu Server and just wanted to set everything up from scratch again.

I setup the computer, setup Apache, PHP, PhpMyAdmin, MySQL and everything seems to be working great but I can't seem to get my SSH working.  I tried installing OpenSSH-Server and OpenSSH-Client first but then I saw that I only had to install SSH in Ubuntu 7.10 so I remove OpenSSH and tried to install SSH but I always get the same error when I try to start the SSH service.

Here is the error I get when I try to restart the service:
/etc/init.d/ssh: line 63: 12264 Segmentation fault /usr/sbin/sshd -t

Here is the error I get when I simply try to start the service:
/etc/init.d/ssh: line 63: 12264 Segmentation fault start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS [FAIL]

Does any one know why this is happening to me or if there is a fix for this?

With kind regards,
Magnus

---

