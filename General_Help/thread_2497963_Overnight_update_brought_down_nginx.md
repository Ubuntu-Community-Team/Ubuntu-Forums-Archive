---
title: "Overnight update brought down nginx"
date: 2024-05-24
forum: General Help
---

### Post by triatic on 2024-05-24
This morning, nginx wan't working, so I checked the journal. It appears an overnight unattended-upgrade stopped and started a lot of services, including systemd-networkd and nginx. Logs pasted at the end.

I bind nginx to specific IP addresses, because different daemons listen on different addresses. When nginx was brought back up, it failed because the requested IPv6 address had not yet come back up.

Am I right in thinking this happened because the system attempted to launch nginx while [COLOR=#000000][FONT=&amp]systemd-networkd.service was stopped?[/FONT][/COLOR] And are there any modifications I can make to my system to avoid reoccurrence (other than performing apt updates manually)?

```
May 24 06:27:54 alpha systemd[1]: Stopping packagekit.service - PackageKit Daemon...May 24 06:27:54 alpha systemd[1]: packagekit.service: Deactivated successfully.
May 24 06:27:54 alpha systemd[1]: Stopped packagekit.service - PackageKit Daemon.
May 24 06:27:54 alpha systemd[1]: exim4.service: Deactivated successfully.
May 24 06:27:54 alpha systemd[1]: Stopped exim4.service - exim Mail Transport Agent.
May 24 06:27:54 alpha systemd[1]: exim4.service: Consumed 15.241s CPU time, 26.4M memory peak, 0B memory swap peak.
May 24 06:27:54 alpha systemd[1]: Starting exim4.service - exim Mail Transport Agent...
May 24 06:27:54 alpha systemd[1]: Starting packagekit.service - PackageKit Daemon...
May 24 06:27:54 alpha systemd[1]: Stopping php8.3-fpm.service - The PHP 8.3 FastCGI Process Manager...
May 24 06:27:54 alpha systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
May 24 06:27:54 alpha sshd[1427]: Received signal 15; terminating.
May 24 06:27:54 alpha systemd-journald[365]: Journal stopped
May 24 06:27:55 alpha systemd[1]: Stopping systemd-journald.service - Journal Service...
May 24 06:27:55 alpha systemd-journald[365]: Received SIGTERM from PID 1 (systemd).
May 24 06:27:55 alpha systemd[1]: netplan-ovs-cleanup.service - OpenVSwitch configuration for cleanup was skipped because of an unmet condition check (ConditionFileIsExecutable=/usr/bin/ovs-vsctl).
May 24 06:27:55 alpha systemd[1]: systemd-networkd-wait-online.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped systemd-networkd-wait-online.service - Wait for Network to be Configured.
May 24 06:27:55 alpha systemd[1]: Stopping systemd-networkd-wait-online.service - Wait for Network to be Configured...
May 24 06:27:55 alpha systemd[1]: Stopping systemd-networkd.service - Network Configuration...
May 24 06:27:55 alpha systemd[1]: ssh.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
May 24 06:27:55 alpha systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
May 24 06:27:55 alpha systemd[1]: nginx.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped nginx.service - A high performance web server and a reverse proxy server.
May 24 06:27:55 alpha systemd[1]: nginx.service: Consumed 6.168s CPU time, 21.6M memory peak, 0B memory swap peak.
May 24 06:27:55 alpha systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
May 24 06:27:55 alpha systemd[1]: Stopping systemd-timesyncd.service - Network Time Synchronization...
May 24 06:27:55 alpha systemd[1]: systemd-journald.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped systemd-journald.service - Journal Service.
May 24 06:27:55 alpha systemd[1]: systemd-journald.service: Consumed 49.437s CPU time, 173.6M memory peak, 0B memory swap peak.
May 24 06:27:55 alpha systemd[1]: systemd-networkd.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped systemd-networkd.service - Network Configuration.
May 24 06:27:55 alpha systemd[1]: systemd-networkd.service: Consumed 3.016s CPU time, 3.6M memory peak, 0B memory swap peak.
May 24 06:27:55 alpha systemd[1]: systemd-timesyncd.service: Deactivated successfully.
May 24 06:27:55 alpha systemd[1]: Stopped systemd-timesyncd.service - Network Time Synchronization.
May 24 06:27:55 alpha systemd[1]: systemd-timesyncd.service: Consumed 1.742s CPU time, 2.2M memory peak, 0B memory swap peak.
May 24 06:27:55 alpha systemd[1]: Starting systemd-journald.service - Journal Service...
May 24 06:27:55 alpha systemd[1]: Starting systemd-networkd.service - Network Configuration...
May 24 06:27:55 alpha systemd-journald[224525]: Collecting audit messages is disabled.
May 24 06:27:55 alpha systemd[1]: Starting systemd-timesyncd.service - Network Time Synchronization...
May 24 06:27:55 alpha systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
May 24 06:27:55 alpha systemd[1]: nginx.service: Control process exited, code=exited, status=1/FAILURE
May 24 06:27:55 alpha systemd[1]: nginx.service: Failed with result 'exit-code'.
May 24 06:27:55 alpha systemd-journald[224525]: Journal started
May 24 06:27:55 alpha systemd-journald[224525]: System Journal (/var/log/journal/f6231ff3466048acbfd448f890443035) is 173.0M, max 4.0G, 3.8G free.
May 24 06:27:55 alpha systemd[1]: Failed to start nginx.service - A high performance web server and a reverse proxy server.
May 24 06:27:54 alpha systemd-networkd[714]: enp0s6: DHCPv6 lease lost
May 24 06:27:54 alpha named[186157]: received control channel command 'stop'
May 24 06:27:54 alpha named[186157]: no longer listening on 127.0.0.1#53
May 24 06:27:55 alpha nginx[224476]: nginx: [emerg] bind() to [2603:c020:x:x:x:x:x:x]:80 failed (99: Cannot assign requested address)
May 24 06:27:55 alpha nginx[224476]: nginx: configuration file /etc/nginx/nginx.conf test failed
```

---

### Post by TheFu on 2024-05-24
Patching too often is a liability.  unattended-upgrades are dangerous.  Nobody here works for Canonical, so you need to open a critical bug in Landscape if you actually want anyone to do something about it.

I'm glad that we only patch during maintenance windows once a week, over the weekends.  We were burned by an update about 15 yrs ago and learned the lesson after 3 hrs of downtime, when we scheduled/promised just 15 minutes.   For a similar reason, we block snap updates, except on Saturdays.  Wish we had more control over snap updates too.  A few times entire servers were taken down from a bad snap major upgrade that we tried to prevent (we only want minor updates, never between major releases).

---

### Post by triatic on 2024-05-24
> **TheFu said:**
> Patching too often is a liability.  unattended-upgrades are dangerous.  Nobody here works for Canonical, so you need to open a critical bug in Landscape if you actually want anyone to do something about it.

Point taken, although this is the first time I have seen such an issue, and I've used unattended-upgrades for a long time, albeit on non-complex systems. Most people use wildcards for binding addresses, and so they probably would not have seen this manifest.

It seems avoidable, as something simply seems off with the order of restart execution, there's nothing wrong with the updated packages themselves.

I'll take a look at Landscape which is not something I've dealt with, as a non-commercial user of Ubuntu.

---

### Post by TheFu on 2024-05-24
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

When everything goes well, it is definitely more convenient to have automation handle things, but when things break ... well, that's completely different.

---

### Post by triatic on 2024-05-24
My launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/2067057](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/2067057)

---

### Post by TheFu on 2024-05-25
I patched today and none of my nginx servers were impacted.  I run over 20 virtual domains on 20.04 servers.  Hopefully, for important things, you aren't on the bleeding edge.  That would be crazy at this point.  If you do. Thanks for being a tester.

You know there's a system information gathering script that the bug reports will ask for, so they don't have to beg you for 20 standard pieces of information.  You should provide that without them asking.  Also, it would be useful to post the main things here, so we aren't left guessing the most important things.

---

### Post by triatic on 2024-05-25
It's not going to be possible to replicate this unless I have a similar update to perform in future. And even if I did, there's a chance the execution durations alter next time around, by sheer chance, since the service restart order does not appear to be structured.

Most people don't bind nginx or other services to specific IP addresses, they use wildcards. It would not have failed were I using wildcard addresses in nginx, because it would just silently bind to whatever was available at the time.

The log is self explanatory, nginx attempted to bind to a specific IPv6 address that was brought down before it came back. I'm really not sure what other information is of value here.

24.04 LTS is not "bleeding edge" (sorry for not being a tester).

---

### Post by TheFu on 2024-05-25
24.04 **is** bleeding edge for another year, but feel free to have your opinion on that.  New releases are always bleeding for at least 6 months.

---

