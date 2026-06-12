---
title: "cannot install tftpd-hpa -"
date: 2015-06-03
forum: General Help
---

### Post by mrpg99 on 2015-06-03
Dear Sir/Madam,

I am trying to install tftpd-hpa to get a pxe server up and running on my pc.

I am using Ubuntu 15.04 vidid.

Here are some details on what happens :

[22:35:04] mrpg@pgdc001:[/]: sudo apt-get install tftpd-hpa
Reading package lists... Done
Building dependency tree
Reading state information... Done
tftpd-hpa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up tftpd-hpa (5.2+20140608-3ubuntu1) ...
tftpd user (tftp) already exists, doing nothing.


tftpd-hpa directory (/var/lib/tftpboot) already exists, doing nothing.
Job for tftpd-hpa.service failed. See "systemctl status tftpd-hpa.service" and "journalctl -xe" for details.
invoke-rc.d: initscript tftpd-hpa, action "start" failed.
dpkg: error processing package tftpd-hpa (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tftpd-hpa
E: Sub-process /usr/bin/dpkg returned an error code (1)



[22:35:57] mrpg@pgdc001:[/]: systemctl status tftpd-hpa.service
&#9679; tftpd-hpa.service - LSB: HPA's tftp server
   Loaded: loaded (/etc/init.d/tftpd-hpa)
   Active: failed (Result: exit-code) since Wed 2015-06-03 22:35:11 CEST; 48s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 11537 ExecStart=/etc/init.d/tftpd-hpa start (code=exited, status=66)
Jun 03 22:35:11 pgdc001 systemd[1]: Starting LSB: HPA's tftp server...
Jun 03 22:35:11 pgdc001 tftpd-hpa[11537]: * Starting HPA's tftpd in.tftpd
Jun 03 22:35:11 pgdc001 systemd[1]: tftpd-hpa.service: control process exited, code=exi...=66
Jun 03 22:35:11 pgdc001 systemd[1]: Failed to start LSB: HPA's tftp server.
Jun 03 22:35:11 pgdc001 systemd[1]: Unit tftpd-hpa.service entered failed state.
Jun 03 22:35:11 pgdc001 systemd[1]: tftpd-hpa.service failed.
Hint: Some lines were ellipsized, use -l to show in full.


[22:36:40] mrpg@pgdc001:[/]: journalctl -xe
Jun 03 22:35:12 pgdc001 systemd[1]: Started PackageKit Daemon.
-- Subject: Unit packagekit.service has finished start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit packagekit.service has finished starting up.
--
-- The start-up result is done.
Jun 03 22:35:12 pgdc001 sudo[11432]: pam_unix(sudo:session): session closed for user root
Jun 03 22:35:19 pgdc001 systemd[1]: Starting Cleanup of Temporary Directories...
-- Subject: Unit systemd-tmpfiles-clean.service has begun start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit systemd-tmpfiles-clean.service has begun starting up.
Jun 03 22:35:19 pgdc001 systemd-tmpfiles[11629]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate
Jun 03 22:35:19 pgdc001 systemd[1]: Started Cleanup of Temporary Directories.
-- Subject: Unit systemd-tmpfiles-clean.service has finished start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit systemd-tmpfiles-clean.service has finished starting up.
--
-- The start-up result is done.
Jun 03 22:35:19 pgdc001 pkexec[11627]: pam_unix(polkit-1:session): session opened for user ro
Jun 03 22:35:19 pgdc001 pkexec[11627]: pam_ck_connector(polkit-1:session): cannot determine d
Jun 03 22:35:19 pgdc001 pkexec[11627]: mrpg: Executing command [USER=root] [TTY=unknown] [CWD
Jun 03 22:36:09 pgdc001 sm-notify[1775]: Unable to notify pgnas.flashpoint.local, giving up
lines 1152-1179/1179 (END)


have googled for hours and tried all sorts of stuff, but nothing has helped so far.

many thanks for any input!

Best Regards
Patric

---

