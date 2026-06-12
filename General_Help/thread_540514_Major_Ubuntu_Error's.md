---
title: "Major Ubuntu Error's"
date: 2007-09-01
forum: General Help
---

### Post by cawill on 2007-09-01
I recently updated Ubuntu 7.04 and when I rebooted GDM and iptables failed to start, leaving me having to log in shell mode and startx manually and now I have no internet and I'm forced to use the live cd to post this, I have tried another kernel but I get the same problem, can this be fixed or do I need to reinstall? is there anyway I could find out the errors that are causing the problem?

---

### Post by RaZer0r on 2007-09-01
check you syslog using the command:
```

more /var/log/syslog

```

---

### Post by cawill on 2007-09-01
Ok thanks.

syslog file:
```
Sep  1 23:54:12 sony syslogd 1.4.1#20ubuntu4: restart.
Sep  1 23:54:13 sony dhcdbd: dbus_svc_init failed: org.freedesktop.DBus.Error.NoReply Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Sep  1 23:54:13 sony dhcdbd: Failed to initialise D-Bus service. 
Sep  1 23:54:13 sony NetworkManager: <information>^Istarting... 
Sep  1 23:54:13 sony NetworkManager: <WARNING>^I nm_dbus_init (): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Sep  1 23:54:13 sony NetworkManager: <ERROR>^I[1188687253.187475] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded. 
Sep  1 23:54:13 sony NetworkManager: traceback: 
Sep  1 23:54:13 sony NetworkManager: ^I/usr/sbin/NetworkManager(main+0x47f) [0x806916f] 
Sep  1 23:54:13 sony NetworkManager: ^I/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c99ebc] 
Sep  1 23:54:13 sony NetworkManager: ^I/usr/sbin/NetworkManager [0x8053e41] 
Sep  1 23:54:13 sony avahi-daemon[5134]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep  1 23:54:13 sony avahi-daemon[5134]: Successfully dropped root privileges.
Sep  1 23:54:13 sony avahi-daemon[5134]: Failed to create PID file: Permission denied
Sep  1 23:54:14 sony mysqld_safe[5382]: started
Sep  1 23:54:14 sony mysqld[5385]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Sep  1 23:54:14 sony mysqld[5385]: 070901 23:54:14 [ERROR] Aborting
Sep  1 23:54:14 sony mysqld[5385]: 
Sep  1 23:54:14 sony mysqld[5385]: 070901 23:54:14 [Note] /usr/sbin/mysqld: Shutdown complete
Sep  1 23:54:14 sony mysqld[5385]: 
Sep  1 23:54:14 sony mysqld_safe[5388]: ended
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: 
Sep  1 23:54:29 sony exportfs[5715]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.3:/home/chris/share".   Assuming default behaviour ('subtree_check').   NOTE: this default will change with nfs-utils version 1.1.0
Sep  1 23:54:29 sony nfsd[5726]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep  1 23:54:29 sony nfsd[5726]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: PREINIT(1)
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: INIT(2)
Sep  1 23:54:30 sony ntop[5754]:   ntop v.3.2 SourceForge .tgz
Sep  1 23:54:30 sony ntop[5754]:   Configured on Mar  5 2007  7:11:14, built on Mar  5 2007 07:11:47.
Sep  1 23:54:30 sony ntop[5754]:   Copyright 1998-2005 by Luca Deri <deri@ntop.org>
Sep  1 23:54:30 sony ntop[5754]:   Get the freshest ntop from http://www.ntop.org/
Sep  1 23:54:30 sony ntop[5754]:   NOTE: ntop is running from '/usr/sbin'
Sep  1 23:54:30 sony ntop[5754]:   NOTE: (but see warning on man page for the --instance parameter)
Sep  1 23:54:30 sony ntop[5754]:   NOTE: ntop libraries are in '/usr/lib'
Sep  1 23:54:30 sony ntop[5754]:   Initializing ntop
Sep  1 23:54:30 sony ntop[5754]:   PROTO_INIT: Processing protocol file: '/etc/ntop/protocol.list', size: 390
Sep  1 23:54:30 sony ntop[5754]:   **ERROR** pcap_open_live(): 'bind: Network is down'
Sep  1 23:54:30 sony ntop[5754]:   Please correct the problem or select a different interface using the -i flag
Sep  1 23:54:30 sony ntop[5754]:   **FATAL_ERROR** Not root, ntop shutting down...
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP[t3057010896]: ntop caught signal 2
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: SHUTDOWN(7)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP[t3057010896] catching thread is MAIN
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Running threads
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Locking purge mutex (may block for a little while)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Locked purge mutex, continuing shutdown
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Continues
Sep  1 23:54:30 sony ntop[5754]:   FREE_HOST: Start, 1 device(s)
Sep  1 23:54:30 sony ntop[5754]:   FREE_HOST: End, freed 0
Sep  1 23:54:30 sony ntop[5754]:   PLUGIN_TERM: Unloading plugins (if any)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Freeing device eth0 (idx=0)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Clean up complete
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: TERM(8)
Sep  1 23:54:30 sony ntop[5754]:   ===================================
Sep  1 23:54:30 sony ntop[5754]:           ntop is shutdown...        
Sep  1 23:54:30 sony ntop[5754]:   ===================================
Sep  1 23:54:32 sony rpc.statd[5871]: Version 1.0.11 Starting
Sep  1 23:54:32 sony ntpd[5901]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep  1 23:54:32 sony ntpd[5902]: precision = 1.000 usec
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface wildcard, ::#123 Disabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface lo, ::1#123 Enabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep  1 23:54:32 sony ntpd[5902]: kernel time sync status 0040
Sep  1 23:54:32 sony ntpd[5902]: frequency initialized 70.072 PPM from /var/lib/ntp/ntp.drift
Sep  1 23:54:32 sony hcid[5928]: Bluetooth HCI daemon
Sep  1 23:54:32 sony hcid[5928]: Can't connect to system message bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Sep  1 23:54:32 sony hcid[5928]: Unable to get on D-Bus
Sep  1 23:54:33 sony anacron[5967]: Anacron 2.3 started on 2007-09-01
Sep  1 23:54:33 sony anacron[5967]: Normal exit (0 jobs run)
Sep  1 23:54:33 sony /usr/sbin/cron[5991]: (CRON) INFO (pidfile fd = 3)
Sep  1 23:54:33 sony /usr/sbin/cron[5992]: (CRON) STARTUP (fork ok)
Sep  1 23:54:33 sony /usr/sbin/cron[5992]: (CRON) INFO (Running @reboot jobs)
Sep  1 23:54:34 sony ntpd_initres[5910]: host name not found: ntp.ubuntu.com
Sep  1 23:54:34 sony ntpd_initres[5910]: couldn't resolve `ntp.ubuntu.com', giving up on it
Sep  1 23:55:55 sony gconfd (chris-6214): starting (version 2.18.0.1), pid 6214 user 'chris'
Sep  1 23:55:55 sony gconfd (chris-6214): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  1 23:55:55 sony gconfd (chris-6214): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 1
Sep  1 23:55:55 sony gconfd (chris-6214): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  1 23:55:55 sony gconfd (chris-6214): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  1 23:55:55 sony gconfd (chris-6214): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  1 23:56:04 sony gconfd (chris-6214): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 0
Sep  2 00:00:01 sony /USR/SBIN/CRON[6670]: (root) CMD ( test -f /proc/net/ip_tables_names && test -f /etc/ipac-ng/ipac.conf && test -f /usr/sbin/fetchipac && test -d /var/lib/ipac/ && /usr/bin/nice /usr/sbin/fetchipac)
Sep  2 00:00:25 sony gconfd (root-6685): starting (version 2.18.0.1), pid 6685 user 'root'
Sep  2 00:00:25 sony gconfd (root-6685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  2 00:00:25 sony gconfd (root-6685): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep  2 00:00:25 sony gconfd (root-6685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  2 00:00:25 sony gconfd (root-6685): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  2 00:00:25 sony gconfd (root-6685): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  2 00:01:55 sony gconfd (root-6685): GConf server is not in use, shutting down.
Sep  2 00:01:55 sony gconfd (root-6685): Exiting
```

My daemon.log
```
Sep  1 23:54:13 sony NetworkManager: <information>^Istarting... 
Sep  1 23:54:13 sony NetworkManager: <WARNING>^I nm_dbus_init (): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Sep  1 23:54:13 sony NetworkManager: <ERROR>^I[1188687253.187475] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded. 
Sep  1 23:54:13 sony NetworkManager: traceback: 
Sep  1 23:54:13 sony NetworkManager: ^I/usr/sbin/NetworkManager(main+0x47f) [0x806916f] 
Sep  1 23:54:13 sony NetworkManager: ^I/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c99ebc] 
Sep  1 23:54:13 sony NetworkManager: ^I/usr/sbin/NetworkManager [0x8053e41] 
Sep  1 23:54:13 sony avahi-daemon[5134]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Sep  1 23:54:13 sony avahi-daemon[5134]: Successfully dropped root privileges.
Sep  1 23:54:13 sony avahi-daemon[5134]: Failed to create PID file: Permission denied
Sep  1 23:54:14 sony mysqld_safe[5382]: started
Sep  1 23:54:14 sony mysqld[5385]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Sep  1 23:54:14 sony mysqld[5385]: 070901 23:54:14 [ERROR] Aborting
Sep  1 23:54:14 sony mysqld[5385]: 
Sep  1 23:54:14 sony mysqld[5385]: 070901 23:54:14 [Note] /usr/sbin/mysqld: Shutdown complete
Sep  1 23:54:14 sony mysqld[5385]: 
Sep  1 23:54:14 sony mysqld_safe[5388]: ended
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Sep  1 23:54:28 sony /etc/init.d/mysql[5538]: 
Sep  1 23:54:29 sony exportfs[5715]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.3:/home/chris/share".   Assuming default behaviour ('subtree_check').   NOTE: this default will change with nfs-utils version 1.1.0
Sep  1 23:54:29 sony nfsd[5726]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep  1 23:54:29 sony nfsd[5726]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Sep  1 23:54:30 sony ntop[5754]:   ntop v.3.2 SourceForge .tgz
Sep  1 23:54:30 sony ntop[5754]:   Configured on Mar  5 2007  7:11:14, built on Mar  5 2007 07:11:47.
Sep  1 23:54:30 sony ntop[5754]:   Copyright 1998-2005 by Luca Deri <deri@ntop.org>
Sep  1 23:54:30 sony ntop[5754]:   Get the freshest ntop from [http://www.ntop.org/](http://www.ntop.org/)
Sep  1 23:54:30 sony ntop[5754]:   NOTE: ntop is running from '/usr/sbin'
Sep  1 23:54:30 sony ntop[5754]:   NOTE: (but see warning on man page for the --instance parameter)
Sep  1 23:54:30 sony ntop[5754]:   NOTE: ntop libraries are in '/usr/lib'
Sep  1 23:54:30 sony ntop[5754]:   Initializing ntop
Sep  1 23:54:30 sony ntop[5754]:   PROTO_INIT: Processing protocol file: '/etc/ntop/protocol.list', size: 390
Sep  1 23:54:30 sony ntop[5754]:   **ERROR** pcap_open_live(): 'bind: Network is down'
Sep  1 23:54:30 sony ntop[5754]:   Please correct the problem or select a different interface using the -i flag
Sep  1 23:54:30 sony ntop[5754]:   **FATAL_ERROR** Not root, ntop shutting down...
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP[t3057010896]: ntop caught signal 2
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: SHUTDOWN(7)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP[t3057010896] catching thread is MAIN
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Running threads
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Locking purge mutex (may block for a little while)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Locked purge mutex, continuing shutdown
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Continues
Sep  1 23:54:30 sony ntop[5754]:   FREE_HOST: Start, 1 device(s)
Sep  1 23:54:30 sony ntop[5754]:   FREE_HOST: End, freed 0
Sep  1 23:54:30 sony ntop[5754]:   PLUGIN_TERM: Unloading plugins (if any)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Freeing device eth0 (idx=0)
Sep  1 23:54:30 sony ntop[5754]:   CLEANUP: Clean up complete
Sep  1 23:54:30 sony ntop[5754]:   THREADMGMT[t3057010896]: ntop RUNSTATE: TERM(8)
Sep  1 23:54:30 sony ntop[5754]:   ===================================
Sep  1 23:54:30 sony ntop[5754]:           ntop is shutdown...        
Sep  1 23:54:30 sony ntop[5754]:   ===================================
Sep  1 23:54:32 sony rpc.statd[5871]: Version 1.0.11 Starting
Sep  1 23:54:32 sony ntpd[5901]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Sep  1 23:54:32 sony ntpd[5902]: precision = 1.000 usec
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface wildcard, ::#123 Disabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface lo, ::1#123 Enabled
Sep  1 23:54:32 sony ntpd[5902]: Listening on interface lo, 127.0.0.1#123 Enabled
Sep  1 23:54:32 sony ntpd[5902]: kernel time sync status 0040
Sep  1 23:54:32 sony ntpd[5902]: frequency initialized 70.072 PPM from /var/lib/ntp/ntp.drift
Sep  1 23:54:32 sony hcid[5928]: Bluetooth HCI daemon
Sep  1 23:54:32 sony hcid[5928]: Can't connect to system message bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Sep  1 23:54:32 sony hcid[5928]: Unable to get on D-Bus
Sep  1 23:54:34 sony ntpd_initres[5910]: host name not found: ntp.ubuntu.com
Sep  1 23:54:34 sony ntpd_initres[5910]: couldn't resolve `ntp.ubuntu.com', giving up on it
```

Can anyone work out what is wrong and how to fix this?

Thanks in advance, Chris.

---

### Post by cawill on 2007-09-02
Bump, can anyone help?

---

### Post by cawill on 2007-09-02
It seems I am having permission errors and programs are telling me that I don't have the permission to run things even as root, is there a way to reconfigure the permissions of the whole system?

The problem is nearly the same as [This Thread]("http://ubuntuforums.org/showthread.php?t=409350")

---

