---
title: "xubuntu random reboots when unattended"
date: 2019-07-04
forum: General Help
---

### Post by arst06d on 2019-07-04
Hi

Installed xubuntu 18.04 LTS on my laptop 9 months ago.  Over the past month there have been many times when I come back to the laptop to find it has rebooted/restarted, all applications closed whetherf there was activity (eg video processing) or not going on at the time.

I have never had the issue of the laptop rebooteing when I have been actively using it.

The laptop is permanently running on mains power and I have Power Management set to never suspend when on mains power.

I update regularly and am not running games etc - just browsing, email, LibreOffice and KdenLive (video editing) but nothing outside the capabilities of the laptop.

Any ideas where to start?

Thanks in advance

---

### Post by &amp;wP*!) on 2019-07-04
Despite mains power maybe there is an issue related to your power management setting. Without having your system log it is very difficult to give a clue.

Copy-paste the part your **/var/log/syslog** (you can use [http://pastebin.com]("http://pastebin.com") ) during such an unattended reboot. It will be then easier for us to help you.

---

### Post by arst06d on 2019-07-05
Hi

Hope this helps: 

```
Jul  5 00:08:06 david-N2x0WU rsyslogd:  [origin software="rsyslogd" swVersion="8.32.0" x-pid="727" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul  5 00:08:09 david-N2x0WU anacron[1123]: Job `cron.daily' terminated
Jul  5 00:13:05 david-N2x0WU anacron[1123]: Job `cron.weekly' started
Jul  5 00:13:05 david-N2x0WU anacron[1321]: Updated timestamp for job `cron.weekly' to 2019-07-05
Jul  5 00:13:06 david-N2x0WU anacron[1123]: Job `cron.weekly' terminated
Jul  5 00:13:06 david-N2x0WU anacron[1123]: Normal exit (2 jobs run)
Jul  5 00:17:01 david-N2x0WU CRON[1330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> Received signal: wake up
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> ClamAV update process started at Fri Jul  5 00:17:40 2019
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 00:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 00:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 01:03:35 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 01:03:35 david-N2x0WU anacron[1342]: Anacron 2.3 started on 2019-07-05
Jul  5 01:03:35 david-N2x0WU anacron[1342]: Normal exit (0 jobs run)
Jul  5 01:17:01 david-N2x0WU CRON[1349]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> Received signal: wake up
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> ClamAV update process started at Fri Jul  5 01:17:40 2019
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 01:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 01:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 02:02:13 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 02:02:13 david-N2x0WU anacron[1359]: Anacron 2.3 started on 2019-07-05
Jul  5 02:02:13 david-N2x0WU anacron[1359]: Normal exit (0 jobs run)
Jul  5 02:08:01 david-N2x0WU CRON[1363]: (root) CMD (   test -x /etc/cron.daily/popularity-contest && /etc/cron.daily/popularity-contest --crond)
Jul  5 02:17:01 david-N2x0WU CRON[1369]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> Received signal: wake up
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> ClamAV update process started at Fri Jul  5 02:17:40 2019
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 02:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 02:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 03:00:58 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 03:00:58 david-N2x0WU anacron[1380]: Anacron 2.3 started on 2019-07-05
Jul  5 03:00:58 david-N2x0WU anacron[1380]: Normal exit (0 jobs run)
Jul  5 03:17:01 david-N2x0WU CRON[1385]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> Received signal: wake up
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> ClamAV update process started at Fri Jul  5 03:17:40 2019
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 03:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 03:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 04:02:05 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 04:02:05 david-N2x0WU anacron[1395]: Anacron 2.3 started on 2019-07-05
Jul  5 04:02:05 david-N2x0WU anacron[1395]: Normal exit (0 jobs run)
Jul  5 04:17:01 david-N2x0WU CRON[1402]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> Received signal: wake up
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> ClamAV update process started at Fri Jul  5 04:17:40 2019
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 04:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 04:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 05:02:05 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 05:02:05 david-N2x0WU anacron[1412]: Anacron 2.3 started on 2019-07-05
Jul  5 05:02:05 david-N2x0WU anacron[1412]: Normal exit (0 jobs run)
Jul  5 05:17:01 david-N2x0WU CRON[1420]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> Received signal: wake up
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> ClamAV update process started at Fri Jul  5 05:17:40 2019
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 05:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 05:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 05:22:36 david-N2x0WU snapd[778]: storehelpers.go:441: cannot refresh: snap has no updates available: "asunder-casept", "audacity", "chromium", "core", "core18", "freac", "gimp", "gtk-common-themes", "gtk2-common-themes", "vuze-vs"
Jul  5 05:22:36 david-N2x0WU snapd[778]: autorefresh.go:389: auto-refresh: all snaps are up-to-date
Jul  5 06:00:01 david-N2x0WU CRON[1434]: (david) CMD (/usr/bin/clamscan --exclude-dir=/home/david/.clamtk/viruses --exclude-dir=smb4k --exclude-dir=/run/user/david/gvfs --exclude-dir=/home/david/.gvfs --exclude-dir=.thunderbird --exclude-dir=.mozilla-thunderbird --exclude-dir=.evolution --exclude-dir=Mail --exclude-dir=kmail -i -r /home/david --log="$HOME/.clamtk/history/$(date +%b-%d-%Y).log" 2>/dev/null # clamtk-scan)
Jul  5 06:01:02 david-N2x0WU systemd[1]: Started Run anacron jobs.
Jul  5 06:01:02 david-N2x0WU anacron[1439]: Anacron 2.3 started on 2019-07-05
Jul  5 06:01:02 david-N2x0WU anacron[1439]: Normal exit (0 jobs run)
Jul  5 06:10:36 david-N2x0WU systemd[1]: Starting Daily apt upgrade and clean activities...
Jul  5 06:10:39 david-N2x0WU systemd[1]: Started Daily apt upgrade and clean activities.
Jul  5 06:15:59 david-N2x0WU CRON[1433]: (CRON) info (No MTA installed, discarding output)
Jul  5 06:17:01 david-N2x0WU CRON[1539]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> Received signal: wake up
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> ClamAV update process started at Fri Jul  5 06:17:40 2019
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> ^Your ClamAV installation is OUTDATED!
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.2
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> DON'T PANIC! Read [https://www.clamav.net/documents/upgrading-clamav](https://www.clamav.net/documents/upgrading-clamav)
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> daily.cld is up to date (version: 25500, sigs: 1610180, f-level: 63, builder: raynman)
Jul  5 06:17:40 david-N2x0WU freshclam[715]: Fri Jul  5 06:17:40 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Jul  5 06:25:01 david-N2x0WU CRON[1545]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul  5 06:51:53 david-N2x0WU systemd[1]: session-c1.scope: Killing process 940 (lightdm) with signal SIGTERM.
Jul  5 06:51:53 david-N2x0WU systemd[1]: session-c1.scope: Killing process 975 (lightdm-greeter) with signal SIGTERM.
Jul  5 06:51:53 david-N2x0WU systemd[1]: session-c1.scope: Killing process 976 (lightdm-gtk-gre) with signal SIGTERM.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Stopping Session c1 of user lightdm.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Stopped Session c1 of user lightdm.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Created slice User Slice of david.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Starting User Manager for UID 1000...
Jul  5 06:51:53 david-N2x0WU systemd[1]: Started Session c2 of user david.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Stopping User Manager for UID 110...
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopping Virtual filesystem service...
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopping D-Bus User Message Bus...
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped target Default.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopping Accessibility services bus...
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped D-Bus User Message Bus.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped Accessibility services bus.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Starting D-Bus User Message Bus Socket.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Reached target Timers.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Reached target Paths.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on GnuPG cryptographic agent and passphrase cache.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on GnuPG network certificate management daemon.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped Virtual filesystem service.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped target Basic System.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped target Timers.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped target Paths.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Stopped target Sockets.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed GnuPG network certificate management daemon.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed GnuPG cryptographic agent and passphrase cache.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Jul  5 06:51:53 david-N2x0WU systemd[958]: Closed D-Bus User Message Bus Socket.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Reached target Shutdown.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Starting Exit the Session...
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Listening on D-Bus User Message Bus Socket.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Reached target Sockets.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Reached target Basic System.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Reached target Default.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Startup finished in 30ms.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Started User Manager for UID 1000.
Jul  5 06:51:53 david-N2x0WU systemd[958]: Received SIGRTMIN+24 from PID 1570 (kill).
Jul  5 06:51:53 david-N2x0WU systemd[1]: Stopped User Manager for UID 110.
Jul  5 06:51:53 david-N2x0WU systemd[1]: Removed slice User Slice of lightdm.
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Started D-Bus User Message Bus.
Jul  5 06:51:53 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] AppArmor D-Bus mediation is enabled
Jul  5 06:51:53 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating service name='org.xfce.Xfconf' requested by ':1.4' (uid=1000 pid=1677 comm="xfce4-session " label="unconfined")
Jul  5 06:51:53 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.xfce.Xfconf'
Jul  5 06:51:53 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.11' (uid=1000 pid=1699 comm="/usr/lib/policykit-1-gnome/polkit-gnome-authentica" label="unconfined")
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Starting Accessibility services bus...
Jul  5 06:51:53 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.a11y.Bus'
Jul  5 06:51:53 david-N2x0WU systemd[1554]: Started Accessibility services bus.
Jul  5 06:51:53 david-N2x0WU dbus-daemon[760]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.58' (uid=1000 pid=1723 comm="/usr/bin/pulseaudio --start --log-target=syslog " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[760]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  5 06:51:54 david-N2x0WU systemd[1]: Started RealtimeKit Scheduling Policy Service.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully called chroot.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully dropped privileges.
Jul  5 06:51:54 david-N2x0WU at-spi-bus-launcher[1715]: dbus-daemon[1724]: Activating service name='org.a11y.atspi.Registry' requested by ':1.1' (uid=1000 pid=1701 comm="nm-applet " label="unconfined")
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully limited resources.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Running.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Canary thread running.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Watchdog thread running.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully made thread 1723 of process 1723 (n/a) owned by '1000' high priority at nice level -11.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Supervising 1 threads of 1 processes of 1 users.
Jul  5 06:51:54 david-N2x0WU at-spi-bus-launcher[1715]: dbus-daemon[1724]: Successfully activated service 'org.a11y.atspi.Registry'
Jul  5 06:51:54 david-N2x0WU at-spi-bus-launcher[1715]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.17' (uid=1000 pid=1701 comm="nm-applet " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service...
Jul  5 06:51:54 david-N2x0WU spice-vdagent[1747]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating service name='ca.desrt.dconf' requested by ':1.19' (uid=1000 pid=1726 comm="light-locker " label="unconfined")
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'ca.desrt.dconf'
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.Daemon'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[760]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service' requested by ':1.61' (uid=1000 pid=1700 comm="xfsettingsd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1]: Starting Daemon for power management...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating service name='org.freedesktop.thumbnails.Thumbnailer1' requested by ':1.28' (uid=1000 pid=1696 comm="xfdesktop " label="unconfined")
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.freedesktop.Notifications' unit='xfce4-notifyd.service' requested by ':1.26' (uid=1000 pid=1740 comm="xfce4-power-manager " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting XFCE notifications service...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.freedesktop.Notifications'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started XFCE notifications service.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[760]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  5 06:51:54 david-N2x0WU systemd[1]: Started Daemon for power management.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Supervising 1 threads of 1 processes of 1 users.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully made thread 1829 of process 1723 (n/a) owned by '1000' RT at priority 5.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Supervising 2 threads of 1 processes of 1 users.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Supervising 2 threads of 1 processes of 1 users.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Successfully made thread 1830 of process 1723 (n/a) owned by '1000' RT at priority 5.
Jul  5 06:51:54 david-N2x0WU rtkit-daemon[1725]: Supervising 3 threads of 1 processes of 1 users.
Jul  5 06:51:54 david-N2x0WU bluetoothd[749]: Endpoint registered: sender=:1.68 path=/MediaEndpoint/A2DPSource
Jul  5 06:51:54 david-N2x0WU bluetoothd[749]: Endpoint registered: sender=:1.68 path=/MediaEndpoint/A2DPSink
Jul  5 06:51:54 david-N2x0WU pulseaudio[1723]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Jul  5 06:51:54 david-N2x0WU kernel: [27264.286007] Bluetooth: RFCOMM TTY layer initialized
Jul  5 06:51:54 david-N2x0WU kernel: [27264.286013] Bluetooth: RFCOMM socket layer initialized
Jul  5 06:51:54 david-N2x0WU kernel: [27264.286017] Bluetooth: RFCOMM ver 1.11
Jul  5 06:51:54 david-N2x0WU org.freedesktop.thumbnails.Thumbnailer1[1592]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Jul  5 06:51:54 david-N2x0WU org.freedesktop.thumbnails.Thumbnailer1[1592]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Jul  5 06:51:54 david-N2x0WU org.freedesktop.thumbnails.Thumbnailer1[1592]: Registered thumbailer gnome-thumbnail-font --size %s %u %o
Jul  5 06:51:54 david-N2x0WU org.freedesktop.thumbnails.Thumbnailer1[1592]: Registered thumbailer atril-thumbnailer -s %s %u %o
Jul  5 06:51:54 david-N2x0WU org.freedesktop.thumbnails.Thumbnailer1[1592]: Registered thumbailer /usr/share/blender/scripts/blender-thumbnailer.py %i %o
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.30' (uid=1000 pid=1788 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service - disk device monitor...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service - disk device monitor.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.30' (uid=1000 pid=1788 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service - digital camera monitor...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service - digital camera monitor.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.30' (uid=1000 pid=1788 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service - GNOME Online Accounts monitor...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service - GNOME Online Accounts monitor.
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Indicator Messages Service.
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Reached target Target to start indicators for the xfce4-indicator-plugin.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.30' (uid=1000 pid=1788 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service - Apple File Conduit monitor...
Jul  5 06:51:54 david-N2x0WU gvfs-afc-volume-monitor[1880]: Volume monitor alive
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service - Apple File Conduit monitor.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.30' (uid=1000 pid=1788 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem service - Media Transfer Protocol monitor...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem service - Media Transfer Protocol monitor.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.freedesktop.thumbnails.Thumbnailer1'
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.bluez.obex' unit='dbus-org.bluez.obex.service' requested by ':1.40' (uid=1000 pid=1714 comm="/usr/bin/python3 /usr/bin/blueman-applet " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Bluetooth OBEX service...
Jul  5 06:51:54 david-N2x0WU obexd[1901]: OBEX daemon 5.48
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.bluez.obex'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Bluetooth OBEX service.
Jul  5 06:51:54 david-N2x0WU dbus-daemon[760]: [system] Activating service name='org.blueman.Mechanism' requested by ':1.73' (uid=1000 pid=1714 comm="/usr/bin/python3 /usr/bin/blueman-applet " label="unconfined") (using servicehelper)
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.9' (uid=1000 pid=1696 comm="xfdesktop " label="unconfined")
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Starting Virtual filesystem metadata service...
Jul  5 06:51:54 david-N2x0WU dbus-daemon[1592]: [session uid=1000 pid=1592] Successfully activated service 'org.gtk.vfs.Metadata'
Jul  5 06:51:54 david-N2x0WU systemd[1554]: Started Virtual filesystem metadata service.
Jul  5 06:51:54 david-N2x0WU org.blueman.Mechanism[760]: Unable to init server: Could not connect: Connection refused
Jul  5 06:51:54 david-N2x0WU org.blueman.Mechanism[760]: Unable to init server: Could not connect: Connection refused
Jul  5 06:51:54 david-N2x0WU blueman-mechanism: Starting blueman-mechanism
Jul  5 06:51:54 david-N2x0WU dbus-daemon[760]: [system] Successfully activated service 'org.blueman.Mechanism'
Jul  5 06:51:54 david-N2x0WU blueman-mechani[1907]: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jul  5 06:51:54 david-N2x0WU blueman-mechanism: loading Ppp
Jul  5 06:51:54 david-N2x0WU blueman-mechanism: loading RfKill
Jul  5 06:51:54 david-N2x0WU blueman-mechanism: loading Network
Jul  5 06:51:54 david-N2x0WU blueman-mechanism: loading Rfcomm
Jul  5 06:51:57 david-N2x0WU systemd[1]: Started Daemon for generating UUIDs.
Jul  5 06:52:24 david-N2x0WU blueman-mechanism: Exiting
```

---

### Post by wildmanne39 on 2019-07-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by arst06d on 2019-07-05
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Noted, thanks

---

### Post by &amp;wP*!) on 2019-07-09
You have anti-virus Software ClamAV (which is outdated).
For testing, uninstall it and see whether it fixes your problem.

---

### Post by arst06d on 2019-07-09
I changed the power management settings to never blank the display - it is now permanently on - and the problem has stopped so I'm not sure anything to do with Clam.  The note that it is out of date relates to the fact that it updates itself when it needs to, so just recognising the fact - I think!

---

### Post by arst06d on 2019-07-12
Several days with no unexpected restarts - but with the display permanently on!

Set the "Blank Display After ..." setting to 5 minutes and left it.  Came back - all applications closed down and OS restarted.  I have now turned off Power Management but the permanently on screen is a pain!

---

### Post by arst06d on 2020-04-29
I installed the Screensaver from Software and am running that.

---

