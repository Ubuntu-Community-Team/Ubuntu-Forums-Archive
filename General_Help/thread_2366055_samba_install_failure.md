---
title: "samba install failure"
date: 2017-07-13
forum: General Help
---

### Post by chemprof1981 on 2017-07-13
Hi all,

I am getting this error when trying to install samba file sharing.  Please help!

```
Setting up samba (2:4.3.11+dfsg-0ubuntu0.16.04.8) ...
Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
&#9679; smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
   Loaded: loaded (/etc/init.d/smbd; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2017-07-13 11:33:27 EDT; 7ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 21393 ExecStart=/etc/init.d/smbd start (code=exited, status=1/FAILURE)

Jul 13 11:33:27 xbmc systemd[1]: Starting LSB: start Samba SMB/CIFS daemon (smbd)...
Jul 13 11:33:27 xbmc smbd[21393]:  * Starting SMB/CIFS daemon smbd
Jul 13 11:33:27 xbmc smbd[21393]:    ...fail!
Jul 13 11:33:27 xbmc systemd[1]: smbd.service: Control process exited, code=exited status=1
Jul 13 11:33:27 xbmc systemd[1]: Failed to start LSB: start Samba SMB/CIFS daemon (smbd).
Jul 13 11:33:27 xbmc systemd[1]: smbd.service: Unit entered failed state.
Jul 13 11:33:27 xbmc systemd[1]: smbd.service: Failed with result 'exit-code'.
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up attr (1:2.4.47-2) ...
Setting up libaio1:amd64 (0.3.110-2) ...
Setting up samba-dsdb-modules (2:4.3.11+dfsg-0ubuntu0.16.04.8) ...
Setting up samba-vfs-modules (2:4.3.11+dfsg-0ubuntu0.16.04.8) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

What am I doing wrong?

---

