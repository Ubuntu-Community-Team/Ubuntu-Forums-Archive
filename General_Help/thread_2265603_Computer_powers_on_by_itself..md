---
title: "Computer powers on by itself."
date: 2015-02-16
forum: General Help
---

### Post by gene10 on 2015-02-16
Hi,

a few weeks ago my computer started to turn itself on. Basically, I turn it on, work for a while and than power it off. Next day it turns itself on at exactly same time as I turned it on the previous day. I don't remember changing any settings or anything. It looks like this when I run "last":

reboot   system boot  3.13.0-45-generi Mon Feb 16 11:17 - 11:56  (00:38)
...                     pts/9        :0               Sun Feb 15 12:00 - 13:48  (01:48)
...                     pts/6        :0               Sun Feb 15 11:18 - down   (09:16)
...                       :0           :0               Sun Feb 15 11:17 - down   (09:17)
reboot   system boot  3.13.0-45-generi Sun Feb 15 11:17 - 20:34  (09:17)

The first boot occurred when I pressed the power button on my HP pavilion, and I have no idea what triggered the second one.

I checked all bios settings and turned off every automatic power on feature (actually they were all off to start with).

I am running this version: Linux sdm 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

One strange things is that the computer shuts down very quickly, in around a second. I never paid attention before this started to happen, but it used to take much longer a while ago (on a different machine) when I was still paying attention to these things.

I checked syslog - don't see anything obvious there, but I am not an expert. Below are a few lines from syslog around the shutdown time:

Feb 15 20:33:12 sdm dhclient: DHCPREQUEST of 192.168.1.122 on wlan0 to 192.168.1.1 port 67 (xid=0x1f916b00)Feb 15 20:33:12 sdm dhclient: DHCPACK of 192.168.1.122 from 192.168.1.1
Feb 15 20:33:12 sdm dhclient: bound to 192.168.1.122 -- renewal in 37305 seconds.
Feb 15 20:33:12 sdm NetworkManager[1225]: <info> (wlan0): DHCPv4 state changed reboot -> renew
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   address 192.168.1.122
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   prefix 24 (255.255.255.0)
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   gateway 192.168.1.1
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   nameserver '167....'
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   nameserver '167....'
Feb 15 20:33:12 sdm NetworkManager[1225]: <info>   nameserver '192.168.1.1'
Feb 15 20:33:12 sdm dbus[897]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 15 20:33:12 sdm dbus[897]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 15 20:34:34 sdm avahi-daemon[1029]: Invalid response packet from host 192.168.1.123.
Feb 15 20:34:34 sdm avahi-daemon[1029]: Invalid response packet from host fe80:...
Feb 15 20:34:35 sdm avahi-daemon[1029]: Invalid response packet from host 192.168.1.123.
Feb 15 20:34:35 sdm avahi-daemon[1029]: Invalid response packet from host fe80::...
Feb 15 20:34:41 sdm avahi-daemon[1029]: Invalid response packet from host 192.168.1.123.
Feb 15 20:34:41 sdm avahi-daemon[1029]: Invalid response packet from host fe80::...
Feb 15 11:24:37 sdm rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="899" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Feb 15 20:34:59 sdm rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="899" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb 16 11:17:49 sdm rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="882" x-info="http://www.rsyslog.com"] start
Feb 16 11:17:49 sdm rsyslogd: rsyslogd's groupid changed to 103
Feb 16 11:17:49 sdm rsyslogd: rsyslogd's userid changed to 101
Feb 16 11:17:49 sdm kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 16 11:17:49 sdm kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 16 11:17:49 sdm kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 16 11:17:49 sdm kernel: [    0.000000] Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13)
Feb 16 11:17:49 sdm kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=0c746d80-0952-4ade-835d-89422341dc3d ro quiet splash vt.handoff=7
Feb 16 11:17:49 sdm kernel: [    0.000000] KERNEL supported cpus:
Feb 16 11:17:49 sdm kernel: [    0.000000]   Intel GenuineIntel
Feb 16 11:17:49 sdm kernel: [    0.000000]   AMD AuthenticAMD
Feb 16 11:17:49 sdm kernel: [    0.000000]   Centaur CentaurHauls



I searched the web and didn't find anything obviously relevant. At this point I don't know where to look and will appreciate any help.

Thank you.

---

