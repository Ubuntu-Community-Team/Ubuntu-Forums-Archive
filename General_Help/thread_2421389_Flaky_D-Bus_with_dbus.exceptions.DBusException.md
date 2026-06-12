---
title: "Flaky D-Bus with dbus.exceptions.DBusException"
date: 2019-06-20
forum: General Help
---

### Post by rororo74 on 2019-06-20
[COLOR=#444444][FONT=&amp]**[SYSTEM]** Ubuntu 18.04.2 LTS (GNU/Linux 4.15.0-52-generic x86_64) with all updates

**[PROBLEM] **
**After a reboot, 40% of the times, the D-Bus will fail like so:**[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]
Jun 20 09:28:35 ns1 networkd-dispatcher[679]: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory 
Jun 20 09:28:35 ns1 systemd[1]: networkd-dispatcher.service: Main process exited, code=exited, status=1/FAILURE Jun 20 09:28:35 ns1 systemd[1]: networkd-dispatcher.service: Failed with result 'exit-code'. 
Jun 20 09:28:35 ns1 systemd[1]: Failed to start Dispatcher daemon for systemd-networkd.[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]
Contrast this with the times it succeeds:[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]
Jun 20 09:30:16 ns1 networkd-dispatcher[678]: No valid path found for iwconfig Jun 20 09:30:16 ns1 networkd-dispatcher[678]: No valid path found for iw 
Jun 20 09:30:16 ns1 networkd-dispatcher[678]: WARNING: systemd-networkd is not running, output will be incomplete. 
Jun 20 09:30:16 ns1 systemd[1]: Started Dispatcher daemon for systemd-networkd. 
Jun 20 09:30:16 ns1 systemd[1]: Started firewalld - dynamic firewall daemon.[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]
**[BACKGROUND] **
'Networkd-dispatcher is a dispatcher daemon for systemd-networkd connection status changes.... The daemon listens for signals from systemd-networkd over dbus'[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp][B]
[THEORY] [/B]
So DBus does not start and networkd-dispatcher.service depends on it to service signals... 
When 'Failed to start Dispatcher daemon for systemd-networkd.', firewalld croaks and maybe other things I guess.[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]
**[ACTION] **
I have noticed a pattern that happens when this failure occurs. 
I have attached 2 files... The first with a successful reboot and the second with a failed reboot. 
I have included only messages from 'Started Message of the Day' to the problem area to keep it on target.

How do I resolve this issue?[/FONT][/COLOR]

---

### Post by rororo74 on 2019-06-21
UPDATE: 
I run dozens of tests and I think this is what it boils down to:
This issue is flaky because it seems to depend on the ordering cycle.
The following are the results of the last 10 reboots I conducted. 
**So how do I avoid this vicious cycle from creating havoc?**

OK
Jun 21 05:35:01 ns1 kernel: [    6.892447] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:35:01 ns1 kernel: [    6.917919] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:35:01 ns1 kernel: [    6.933038] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:35:01 ns1 kernel: [    6.971798] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:35:01 ns1 kernel: [    6.992488] systemd[1]: sysinit.target: Found dependency on firewalld.service/stop
Jun 21 05:35:01 ns1 kernel: [    7.002816] systemd[1]: sysinit.target: Found dependency on basic.target/start


OK
Jun 21 05:42:34 ns1 kernel: [    7.513023] systemd[1]: basic.target: Found ordering cycle on paths.target/start
Jun 21 05:42:34 ns1 kernel: [    7.543845] systemd[1]: basic.target: Found dependency on acpid.path/start
Jun 21 05:42:34 ns1 kernel: [    7.572484] systemd[1]: basic.target: Found dependency on sysinit.target/start
Jun 21 05:42:34 ns1 kernel: [    7.597570] systemd[1]: basic.target: Found dependency on cloud-init.service/start
Jun 21 05:42:34 ns1 kernel: [    7.643827] systemd[1]: basic.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:42:34 ns1 kernel: [    7.657047] systemd[1]: basic.target: Found dependency on systemd-networkd.service/start

**ERROR**
**FirewallD reports: Failed to list zones : FirewallD is not running**
Jun 21 05:44:39 ns1 kernel: [    7.396133] **systemd[1]: network-pre.target: Found ordering cycle on firewalld.service/stop**
Jun 21 05:44:39 ns1 kernel: [    7.408784] systemd[1]: network-pre.target: Found dependency on basic.target/start
Jun 21 05:44:39 ns1 kernel: [    7.418770] systemd[1]: network-pre.target: Found dependency on sockets.target/start
Jun 21 05:44:39 ns1 kernel: [    7.455484] systemd[1]: network-pre.target: Found dependency on lxd.socket/start
Jun 21 05:44:39 ns1 kernel: [    7.470305] systemd[1]: network-pre.target: Found dependency on sysinit.target/start
Jun 21 05:44:39 ns1 kernel: [    7.476614] systemd[1]: network-pre.target: Found dependency on cloud-init.service/start

OK with warning
**FirewallD reports: WARNING! Your current IPtables configuration is invalid : iptables-restore v1.6.1: Set f2b-sshd doesn't exist. Error occurred at line: 55**
Jun 21 05:46:40 ns1 kernel: [    7.933542] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:46:40 ns1 kernel: [    7.936860] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:46:40 ns1 kernel: [    7.941158] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:46:40 ns1 kernel: [    7.968777] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:46:40 ns1 kernel: [    7.973984] systemd[1]: sysinit.target: Found dependency on firewalld.service/stop
Jun 21 05:46:40 ns1 kernel: [    7.979068] systemd[1]: sysinit.target: Found dependency on basic.target/start

OK with warning
**FirewallD reports: WARNING! Your current IPtables configuration is invalid : iptables-restore v1.6.1: Set f2b-sshd doesn't exist. Error occurred at line: 55**
Jun 21 05:48:45 ns1 kernel: [    7.233752] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:48:45 ns1 kernel: [    7.246535] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:48:45 ns1 kernel: [    7.265157] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:48:45 ns1 kernel: [    7.272911] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:48:45 ns1 kernel: [    7.281050] systemd[1]: sysinit.target: Found dependency on firewalld.service/stop
Jun 21 05:48:45 ns1 kernel: [    7.288307] systemd[1]: sysinit.target: Found dependency on dbus.service/start


OK
Jun 21 05:50:19 ns1 kernel: [    8.230151] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:50:19 ns1 kernel: [    8.240542] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:50:19 ns1 kernel: [    8.253620] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:50:19 ns1 kernel: [    8.279981] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:50:19 ns1 kernel: [    8.286175] systemd[1]: sysinit.target: Found dependency on firewalld.service/stop
Jun 21 05:50:19 ns1 kernel: [    8.299112] systemd[1]: sysinit.target: Found dependency on dbus.service/start


OK
Jun 21 05:52:07 ns1 kernel: [    7.741061] systemd[1]: basic.target: Found ordering cycle on sockets.target/start
Jun 21 05:52:07 ns1 kernel: [    7.754298] systemd[1]: basic.target: Found dependency on lxd.socket/start
Jun 21 05:52:07 ns1 kernel: [    7.768876] systemd[1]: basic.target: Found dependency on sysinit.target/start
Jun 21 05:52:07 ns1 kernel: [    7.790340] systemd[1]: basic.target: Found dependency on cloud-init.service/start
Jun 21 05:52:07 ns1 kernel: [    7.805422] systemd[1]: basic.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:52:07 ns1 kernel: [    7.840894] systemd[1]: basic.target: Found dependency on systemd-networkd.service/start

**ERROR**
**FirewallD reports: Failed to list zones : Error: DBUS_ERROR: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory**
Jun 21 05:54:11 ns1 kernel: [    8.398419] **systemd[1]: firewalld.service: Found ordering cycle on dbus.socket/start**
Jun 21 05:54:11 ns1 kernel: [    8.404282] systemd[1]: firewalld.service: Found dependency on sysinit.target/start
Jun 21 05:54:11 ns1 kernel: [    8.424332] systemd[1]: firewalld.service: Found dependency on cloud-init.service/start
Jun 21 05:54:11 ns1 kernel: [    8.438320] systemd[1]: firewalld.service: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:54:11 ns1 kernel: [    8.497168] systemd[1]: firewalld.service: Found dependency on systemd-networkd.service/start
Jun 21 05:54:11 ns1 kernel: [    8.505811] systemd[1]: firewalld.service: Found dependency on network-pre.target/start


OK
Jun 21 05:56:09 ns1 kernel: [    7.713971] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:56:09 ns1 kernel: [    7.730411] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:56:09 ns1 kernel: [    7.739376] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:56:09 ns1 kernel: [    7.749455] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:56:09 ns1 kernel: [    7.765509] systemd[1]: sysinit.target: Found dependency on firewalld.service/start
Jun 21 05:56:09 ns1 kernel: [    7.774977] systemd[1]: sysinit.target: Found dependency on dbus.service/start


OK
Jun 21 05:58:02 ns1 kernel: [    7.665025] systemd[1]: sysinit.target: Found ordering cycle on cloud-init.service/start
Jun 21 05:58:02 ns1 kernel: [    7.685481] systemd[1]: sysinit.target: Found dependency on systemd-networkd-wait-online.service/start
Jun 21 05:58:02 ns1 kernel: [    7.692236] systemd[1]: sysinit.target: Found dependency on systemd-networkd.service/start
Jun 21 05:58:02 ns1 kernel: [    7.716383] systemd[1]: sysinit.target: Found dependency on network-pre.target/start
Jun 21 05:58:02 ns1 kernel: [    7.722109] systemd[1]: sysinit.target: Found dependency on firewalld.service/stop
Jun 21 05:58:02 ns1 kernel: [    7.727538] systemd[1]: sysinit.target: Found dependency on basic.target/start

---

