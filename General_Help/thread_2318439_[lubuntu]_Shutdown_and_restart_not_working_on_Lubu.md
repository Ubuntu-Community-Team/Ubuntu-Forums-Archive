---
title: "[lubuntu] Shutdown and restart not working on Lubuntu 14.04 LTS"
date: 2016-03-26
forum: General Help
---

### Post by randomuser12 on 2016-03-26
I just installed fresh Lubuntu 14.04 LTS from USB stick. Checked md5sum and installed via CSM (with UEFI system froze on startup with "select proper boot device" warning message in black screen. I got that fixed).

When I press shutdown or restart, system goes to blue screen with lubuntu logo and five dots keep rolling. That's normal so far. However, when all five dots are blue, dots stop rolling. System completely freezes. When I press ESC at very early stage during shutdown, I got this:

```
wait-for-state stop/waiting
* Stopping ClamAV virus database updater freshclan [OK]
* Stopping rsync daemon rsync [OK]
* Asking all remaining processes to terminate... [OK]
* All processes ended within 1 seconds... [OK]
ModemManager[674]: <info> Caught signal, shutting down... [OK]

ModemManager[674]: <info> ModemManager is shut down

nm.dispatcher.action: Caught signal 15, shutting down...
* Deactivating swap... [OK]
*Will now halt
```

I have waited at least 10 minutes without results.

Only working solution so far has been to shutdown the computer by holding the power button. Pressing ENTER or any key during shutdown doesn't have effect.

Computer is Toshiba Satellite C50-B-12X (PSCMLE-02400EN5)
- Intel® Pentium® N3530  2,16 GHz
- 750 GB hard drive
- 8 192 (1x) MB, DDR3L RAM (1 333 MHz)

Any ideas how to proceed?

---

### Post by Uinthe on 2016-03-26
Show the syslog messages around the shutdown time:
```
tail -n30 /var/log/syslog
```
Any errors or fails during shutdown?

---

### Post by randomuser12 on 2016-03-26
Here it is:

```
valtteri@valtteri-SATELLITE-C50-B:~$ tail -n30 /var/log/syslog
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Canary thread running.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B dbus[607]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Mar 26 13:40:01 valtteri-SATELLITE-C50-B udisksd[1626]: udisks daemon version 2.1.3 starting
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Successfully made thread 1604 of process 1604 (n/a) owned by '1000' high priority at nice level -11.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Supervising 1 threads of 1 processes of 1 users.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B dbus[607]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Mar 26 13:40:01 valtteri-SATELLITE-C50-B udisksd[1626]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Successfully made thread 1649 of process 1604 (n/a) owned by '1000' RT at priority 5.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Supervising 2 threads of 1 processes of 1 users.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Successfully made thread 1652 of process 1604 (n/a) owned by '1000' RT at priority 5.
Mar 26 13:40:01 valtteri-SATELLITE-C50-B rtkit-daemon[1606]: Supervising 3 threads of 1 processes of 1 users.
Mar 26 13:40:07 valtteri-SATELLITE-C50-B NetworkManager[721]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 26 13:40:07 valtteri-SATELLITE-C50-B NetworkManager[721]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 26 13:40:07 valtteri-SATELLITE-C50-B NetworkManager[721]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 26 13:40:07 valtteri-SATELLITE-C50-B NetworkManager[721]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 26 13:40:09 valtteri-SATELLITE-C50-B wpa_supplicant[802]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpdate[1274]: adjust time server 62.237.86.234 offset 0.281668 sec
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1724]: ntpd 4.2.6p5@1.2349-o Thu Feb 11 18:30:40 UTC 2016 (1)
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: proto: precision = 3.073 usec
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen and drop on 1 v6wildcard :: UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen normally on 2 lo 127.0.0.1 UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen normally on 3 wlan0 192.168.11.112 UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen normally on 4 lo ::1 UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listen normally on 5 wlan0 fe80::4ebb:58ff:fe07:5eb6 UDP 123
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: peers refreshed
Mar 26 13:40:10 valtteri-SATELLITE-C50-B ntpd[1725]: Listening on routing socket on fd #22 for interface updates
Mar 26 13:40:17 valtteri-SATELLITE-C50-B ntpd_intres[837]: parent died before we finished, exiting
Mar 26 13:40:18 valtteri-SATELLITE-C50-B kernel: [   48.702186] init: plymouth-stop pre-start process (1779) terminated with status 1

```

---

### Post by Uinthe on 2016-03-26
It could be a problem like mine. Read this topic. In the first and the last posts there are some solutions.
[http://ubuntuforums.org/showthread.php?t=2318255&p=13459881#post13459881](http://ubuntuforums.org/showthread.php?t=2318255&p=13459881#post13459881)

---

### Post by randomuser12 on 2016-03-26
Thanks for the tips Uinthe.

About the last post: I installed sysv-rc-conf and run in terminal "sudo sysv-rc-conf". Reboot was set to level 6 and 'halt' to level 0. So I turned 'halt' to level 6. Then I tried to shut down the computer. This time system froze a lot earlier, during the first blue dot, and after that no key wasn't responding anymore. I tried 'halt' also in level 5, but it didn't make any difference.

So, that didn't work.

---

### Post by Uinthe on 2016-03-26
What about reboot options in /etc/default/grub ? Did u try this way?

---

