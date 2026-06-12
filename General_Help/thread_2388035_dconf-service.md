---
title: "dconf-service"
date: 2018-03-27
forum: General Help
---

### Post by skywalk on 2018-03-27
Hello everyone.
I use Ubuntu 16.04 on a computer with a dual-core AMD processor mounted more than eight years ago.
It will be about two weeks ago that when I start the computer it is appreciated that it is continuously accessing the hard drive and everything is very slow. Some days it behaves like this during the whole work session, others after a certain time, it is normalized. Without any open application System Monitor marks a utilization of 50-60% of CPU. With the top command you can see that dconf-service is continuously writing and Xorg and Compiz consume 10-15% of CPU usage. Today I started the computer at twelve and until three thirty has not regularized its behavior. During this time it has generated a log of more than 35 MiB. I attach the beginning and the end of syslog.
Any help is welcome.
Thank you.

```
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/blkio///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/cpu///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/cpuset///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/devices///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/freezer///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/hugetlb///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/memory///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/net_cls///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/perf_event///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/pids///tasks
Mar 27 12:01:51 jordi-desktop cgmanager[948]: cgmanager:per_ctrl_move_pid_main: pid 7604 (uid 1000 gid 1000) may not write to /run/cgmanager/fs/none,name=systemd///tasks
Mar 27 12:01:51 jordi-desktop org.freedesktop.systemd1[2098]: ** (process:7604): WARNING **: cgmanager method call org.linuxcontainers.cgmanager0_0.MovePidAbs failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: invalid request.  Use G_DBUS_DEBUG=message for more info.
Mar 27 12:01:51 jordi-desktop org.freedesktop.systemd1[2098]: ** (process:7604): WARNING **: cgmanager method call org.linuxcontainers.cgmanager0_0.GetValue failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: invalid request.  Use G_DBUS_DEBUG=message for more info.
Mar 27 12:01:51 jordi-desktop org.freedesktop.systemd1[2098]: ** (process:7604): WARNING **: cgmanager method call org.linuxcontainers.cgmanager0_0.SetValue failed: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: invalid request.  Use G_DBUS_DEBUG=message for more info.
Mar 27 12:01:51 jordi-desktop org.freedesktop.systemd1[2098]: ** (process:7604): CRITICAL **: Unable to acquire bus name 'org.freedesktop.systemd1'.  Quitting.
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: Got existing rate data for sensor: temp1 - rate: 0,139086, last_value 48,000000, last_time 392772448
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: abs rate of change of sensor temp1: 0,199970 (t0: 47,000000, t-1: 48,000000, dv: -1,000000, dt: 5,000760)
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: EWMA abs rate of change of sensor temp1: 0,151262
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: Got existing rate data for sensor: Core0 Temp - rate: 0,466059, last_value 30,000000, last_time 392773255
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: abs rate of change of sensor Core0 Temp: 0,799726 (t0: 26,000000, t-1: 30,000000, dv: -4,000000, dt: 5,001710)
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: EWMA abs rate of change of sensor Core0 Temp: 0,532792
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: Got existing rate data for sensor: Core0 Temp - rate: 0,620254, last_value 28,000000, last_time 392773399
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: abs rate of change of sensor Core0 Temp: 0,999625 (t0: 23,000000, t-1: 28,000000, dv: -5,000000, dt: 5,001878)
Mar 27 12:01:52 jordi-desktop gnome-session[2276]: [dynamic] DEBUG: EWMA abs rate of change of sensor Core0 Temp:
```
```
Mar 27 15:49:07 jordi-desktop gnome-session[1780]: message repeated 2 times: [ (pcmanfm:9140): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: S'ha produït un error a la línia 1: L'entitat no acaba amb un punt i coma. Segurament heu utilitzat un caràcter «&» sense intenció d'iniciar una entitat. Substituïu el caràcter «&» per &amp;.]
Mar 27 16:17:02 jordi-desktop CRON[18307]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 17:00:29 jordi-desktop systemd[1]: dev-disk-by\x2did-wwn\x2d0x5001480000000000.device: Job dev-disk-by\x2did-wwn\x2d0x5001480000000000.device/start timed out.
Mar 27 17:00:29 jordi-desktop systemd[1]: Timed out waiting for device HL-DT-ST_DVDRAM_GH24NSB0.
Mar 27 17:00:29 jordi-desktop systemd[1]: Dependency failed for /mnt/wwn-0x5001480000000000.
Mar 27 17:00:29 jordi-desktop systemd[1]: mnt-wwn\x2d0x5001480000000000.mount: Job mnt-wwn\x2d0x5001480000000000.mount/start failed with result 'dependency'.
Mar 27 17:00:29 jordi-desktop systemd[1]: dev-disk-by\x2did-wwn\x2d0x5001480000000000.device: Job dev-disk-by\x2did-wwn\x2d0x5001480000000000.device/start failed with result 'timeout'.
Mar 27 17:17:01 jordi-desktop CRON[18462]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 17:20:47 jordi-desktop dhclient[1399]: DHCPREQUEST of 192.168.1.36 on eth3 to 192.168.1.1 port 67 (xid=0x28ff7680)
Mar 27 17:20:47 jordi-desktop dhclient[1399]: DHCPACK of 192.168.1.36 from 192.168.1.1
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6225]   address 192.168.1.36
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6226]   plen 24 (255.255.255.0)
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6227]   gateway 192.168.1.1
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6227]   server identifier 192.168.1.1
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6227]   lease time 43200
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6228]   hostname 'jordi-desktop'
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6228]   nameserver '80.58.61.250'
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6229]   nameserver '80.58.61.254'
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6229]   domain name 'homestation'
Mar 27 17:20:47 jordi-desktop NetworkManager[946]: <info>  [1522164047.6352] dhcp4 (eth3): state changed bound -> bound
Mar 27 17:20:47 jordi-desktop dbus[901]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Mar 27 17:20:47 jordi-desktop systemd[1]: Starting Network Manager Script Dispatcher Service...
Mar 27 17:20:47 jordi-desktop dhclient[1399]: bound to 192.168.1.36 -- renewal in 17249 seconds.
Mar 27 17:20:47 jordi-desktop dbus[901]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 27 17:20:47 jordi-desktop systemd[1]: Started Network Manager Script Dispatcher Service.
Mar 27 17:20:47 jordi-desktop nm-dispatcher: req:1 'dhcp4-change' [eth3]: new request (1 scripts)
Mar 27 17:20:47 jordi-desktop nm-dispatcher: req:1 'dhcp4-change' [eth3]: start running ordered scripts...
Mar 27 17:22:17 jordi-desktop systemd[1]: dev-disk-by\x2did-wwn\x2d0x5001480000000000.device: Job dev-disk-by\x2did-wwn\x2d0x5001480000000000.device/start timed out.
Mar 27 17:22:17 jordi-desktop systemd[1]: Timed out waiting for device HL-DT-ST_DVDRAM_GH24NSB0.
Mar 27 17:22:17 jordi-desktop systemd[1]: Dependency failed for /mnt/wwn-0x5001480000000000.
Mar 27 17:22:17 jordi-desktop systemd[1]: mnt-wwn\x2d0x5001480000000000.mount: Job mnt-wwn\x2d0x5001480000000000.mount/start failed with result 'dependency'.
Mar 27 17:22:17 jordi-desktop systemd[1]: dev-disk-by\x2did-wwn\x2d0x5001480000000000.device: Job dev-disk-by\x2did-wwn\x2d0x5001480000000000.device/start failed with result 'timeout'.
Mar 27 17:22:20 jordi-desktop gnome-session[1780]: (pcmanfm:9140): Gtk-CRITICAL **: IA__gtk_window_group_remove_window: assertion 'window->group == window_group' failed
Mar 27 17:29:07 jordi-desktop gnome-session[1780]: ** Message: x-terminal-emulator has very limited support, consider choose another terminal
```

---

