---
title: "dovecot-imapd does not install correctly"
date: 2017-10-05
forum: General Help
---

### Post by csdgbas on 2017-10-05
The following errors occur:

```
Selecting previously unselected package dovecot-imapd.
(Reading database ... 243684 files and directories currently installed.)
Preparing to unpack .../dovecot-imapd_1%3a2.2.27-2ubuntu2_amd64.deb ...
Unpacking dovecot-imapd (1:2.2.27-2ubuntu2) ...
Processing triggers for dovecot-core (1:2.2.27-2ubuntu2) ...
Processing triggers for ufw (0.35-4) ...
Setting up dovecot-imapd (1:2.2.27-2ubuntu2) ...

Creating config file /etc/dovecot/conf.d/20-imap.conf with new version
Processing triggers for dovecot-core (1:2.2.27-2ubuntu2) ...
Job for dovecot.service failed because the control process exited with error code.
See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "restart" failed.
&#9679; dovecot.service - Dovecot IMAP/POP3 email server
   Loaded: loaded (/lib/systemd/system/dovecot.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2017-10-05 14:08:56 BST; 17ms ago
     Docs: man:dovecot(1)
           http://wiki2.dovecot.org/
  Process: 8880 ExecStop=/usr/bin/doveadm stop (code=exited, status=0/SUCCESS)
  Process: 8885 ExecStart=/usr/sbin/dovecot (code=exited, status=89)
 Main PID: 8729 (code=exited, status=0/SUCCESS)

Oct 05 14:08:56 ash systemd[1]: Starting Dovecot IMAP/POP3 email server...
Oct 05 14:08:56 ash dovecot[8885]: Error: socket() failed: Address family n…ocol
Oct 05 14:08:56 ash dovecot[8885]: Error: service(imap-login): listen(::, 1…ocol
Oct 05 14:08:56 ash dovecot[8885]: master: Error: socket() failed: Address …ocol
Oct 05 14:08:56 ash dovecot[8885]: Fatal: Failed to start listeners
Oct 05 14:08:56 ash systemd[1]: dovecot.service: Control process exited, co…s=89
Oct 05 14:08:56 ash systemd[1]: Failed to start Dovecot IMAP/POP3 email server.
Oct 05 14:08:56 ash systemd[1]: dovecot.service: Unit entered failed state.
Oct 05 14:08:56 ash systemd[1]: dovecot.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ufw (0.35-4) ...
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up dovecot-core (1:2.2.27-2ubuntu2) ...
Job for dovecot.service failed because the control process exited with error code.
See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
&#9679; dovecot.service - Dovecot IMAP/POP3 email server
   Loaded: loaded (/lib/systemd/system/dovecot.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2017-10-05 14:09:28 BST; 14ms ago
     Docs: man:dovecot(1)
           http://wiki2.dovecot.org/
  Process: 11297 ExecStart=/usr/sbin/dovecot (code=exited, status=89)
 Main PID: 8729 (code=exited, status=0/SUCCESS)

Oct 05 14:09:28 ash dovecot[11297]: Error: socket() failed: Address family …ocol
Oct 05 14:09:28 ash dovecot[11297]: master: Error: socket() failed: Address…ocol
Oct 05 14:09:28 ash dovecot[11297]: Error: service(imap-login): listen(::, …ocol
Oct 05 14:09:28 ash dovecot[11297]: master: Error: service(imap-login): lis…ocol
Oct 05 14:09:28 ash dovecot[11297]: Fatal: Failed to start listeners
Oct 05 14:09:28 ash dovecot[11297]: master: Fatal: Failed to start listeners
Oct 05 14:09:28 ash systemd[1]: dovecot.service: Control process exited, co…s=89
Oct 05 14:09:28 ash systemd[1]: Failed to start Dovecot IMAP/POP3 email server.
Oct 05 14:09:28 ash systemd[1]: dovecot.service: Unit entered failed state.
Oct 05 14:09:28 ash systemd[1]: dovecot.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-core

```

Ubuntu 17.04, should it make any difference.

---

