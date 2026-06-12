---
title: "can't login as normal user, network down"
date: 2007-04-14
forum: General Help
---

### Post by jpkotta on 2007-04-14
I have almost completely borked my laptop.  Let me start by saying it is definately a configuration issue, because everything works fine with a live CD.  *Almost* everything works as root, which is why I've puzzled (it should be much closer to "everything works as root").  This is Dapper, BTW.

**The last thing I did when it broke.**

I was installing the dynamic DNS client from no-ip.com.  I had done this before on my desktop several months ago and I was putting it on my laptop.  I did the whole `make ; sudo checkinstall` dance.  During the checkinstall, it asked which network interface to use.  The one I wanted (eth0) was not up at the time, so I ctrl-C'ed the install and then things went south.  I suddenly couldn't run *anything* as a normal user.  I tried switching to the console but the lame ATI drivers hung as they are wont to do.  So did a hard reboot and the laptop booted into the console (no gdm).  I have a root password and I can do most things as root.

**Symptoms**

gdm doesn't work.  However, startx as root works.

sudo doesn't work, even as root.  It complains about not having permissions for /etc/sudoers, yet if I chmod them it complains about incorrect permissions.  

I can't do anything as a non-root user.  I have tried login, su, sudo, even local ssh (I think it just uses login), all to no avail.  login complains about not being able to cd to /home/username.  su simply says "No shell".  See above for sudo.  ssh behaves like login.  I have tried this for two different "real" (i.e. general purpose, you can get work done with them) users.  I made a third user just to test with.  I tried starting the folding@home daemon, which runs as its own user, and it always fails.  /home (and everything else) mounts properly.

dbus is broken.  hal fails to startup properly.  I'm not that familiar with what exactly dbus is, so I'll leave it at that.

The network won't come up.  I get errors from dhcdbd about dbus_svc_init in /var/log/syslog.  I get permission errors from /lib/dhcp3-client/call-dhclient-script.  

**Logs**

/var/log/syslog
> Apr 11 18:51:54 localhost sh: 3^Iopen^I/dev/tty^I#success 
Apr 11 18:52:06 localhost tar: -1^Imkdir^I/^I#File exists 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/var^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/var/tmp^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/var/tmp/iEmQLegoinAmGEEHODGA^I#success 
Apr 11 18:52:06 localhost tar: 5^Iopen^I//./no-backup/var/tmp/iEmQLegoinAmGEEHODGA/newfiles.tmp^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/var/tmp/iEmQLegoinAmGEEHODGA/newfiles.tmp^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/var/tmp/iEmQLegoinAmGEEHODGA^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/var/tmp/iEmQLegoinAmGEEHODGA^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/var/tmp^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/var/tmp^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/var^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/var^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/usr^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/usr/local^I#success 
Apr 11 18:52:06 localhost tar: 0^Imkdir^I//./no-backup/usr/local/bin^I#success 
Apr 11 18:52:06 localhost tar: 5^Iopen^I//./no-backup/usr/local/bin/noip2^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/usr/local/bin/noip2^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/usr/local/bin^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/usr/local/bin^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/usr/local^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/usr/local^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup/usr^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup/usr^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/no-backup^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/no-backup^I0^I0^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichmod^I/^I00700^I#success 
Apr 11 18:52:06 localhost tar: 0^Ichown^I/^I0^I0^I#success 
Apr 11 18:52:06 localhost rm: -1^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA^I#Is a directory 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/package^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/installscript.sh^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/var/tmp/iEmQLegoinAmGEEHODGA/newfiles.tmp^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/var/tmp/iEmQLegoinAmGEEHODGA^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/var/tmp^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/var^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/usr/local/bin/noip2^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/usr/local/bin^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/usr/local^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/usr^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/var/tmp/iEmQLegoinAmGEEHODGA/newfiles.tmp^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/var/tmp/iEmQLegoinAmGEEHODGA^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/var/tmp^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/var^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/usr/local/bin/noip2^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/usr/local/bin^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/usr/local^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup/usr^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup/no-backup^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/no-backup^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/var/tmp/iEmQLegoinAmGEEHODGA/package^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/var/tmp/iEmQLegoinAmGEEHODGA/installscript.sh^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/var/tmp/iEmQLegoinAmGEEHODGA^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/var/tmp^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup/var^I#success 
Apr 11 18:52:06 localhost rm: 0^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA/backup^I#success 
Apr 11 18:52:06 localhost rm: 0^Iunlink^I/var/tmp/iEmQLegoinAmGEEHODGA/newfiles.tmp^I#success 
Apr 11 18:52:06 localhost rm: -1^Irmdir^I/var/tmp/iEmQLegoinAmGEEHODGA^I#Directory not empty 
Apr 11 18:52:06 localhost rm: -1^Iunlink^I/home/jpkotta/w/noip-2.1.4/^I#No such file or directory 
Apr 11 18:52:06 localhost rm: -1^Iunlink^I/home/jpkotta/w/noip-2.1.4/checkinstall-debug*^I#No such file or directory 
Apr 11 18:55:42 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr 11 18:55:43 localhost dhcdbd: dbus_svc_init failed: org.freedesktop.DBus.Error.NoReply No reply within specified time
Apr 11 18:55:43 localhost dhcdbd: Failed to initialise D-Bus service. 
Apr 11 18:55:47 localhost anacron[4971]: Anacron 2.3 started on 2007-04-11
Apr 11 18:55:47 localhost anacron[4971]: Normal exit (0 jobs run)
Apr 11 18:55:47 localhost /usr/sbin/cron[5001]: (CRON) INFO (pidfile fd = 3)
Apr 11 18:55:47 localhost /usr/sbin/cron[5002]: (CRON) STARTUP (fork ok)
Apr 11 18:55:47 localhost /usr/sbin/cron[5002]: (CRON) INFO (Running @reboot jobs)
Apr 11 18:55:48 localhost vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 11 18:55:48 localhost vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 18:55:48 localhost vmnet-dhcpd: All rights reserved.
Apr 11 18:55:48 localhost vmnet-dhcpd: 
Apr 11 18:55:48 localhost vmnet-dhcpd: Please contribute if you find this software useful.
Apr 11 18:55:48 localhost vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 18:55:48 localhost vmnet-dhcpd: 
Apr 11 18:55:48 localhost vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 11 18:55:48 localhost vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 18:55:48 localhost vmnet-dhcpd: All rights reserved.
Apr 11 18:55:48 localhost vmnet-dhcpd: 
Apr 11 18:55:48 localhost vmnet-dhcpd: Please contribute if you find this software useful.
Apr 11 18:55:48 localhost vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 18:55:48 localhost vmnet-dhcpd: 
Apr 11 18:55:49 localhost vmnet-dhcpd: Configured subnet: 172.16.74.0
Apr 11 18:55:49 localhost vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.74.254
Apr 11 18:55:49 localhost vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.74.0
Apr 11 18:55:49 localhost vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.74.0
Apr 11 18:55:49 localhost vmnet-dhcpd: Configured subnet: 172.16.220.0
Apr 11 18:55:49 localhost vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.220.254
Apr 11 18:55:49 localhost vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.220.0
Apr 11 18:55:49 localhost vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.220.0
Apr 11 18:56:51 localhost ntpdate[5365]: can't find host ntp.ubuntu.com 
Apr 11 18:56:51 localhost ntpdate[5365]: no servers can be used, exiting
Apr 11 19:02:30 localhost shutdown[5446]: shutting down for system reboot
Apr 11 19:02:30 localhost init: Switching to runlevel: 6
Apr 11 19:02:44 localhost exiting on signal 15
Apr 11 19:03:40 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr 11 19:03:41 localhost dhcdbd: dbus_svc_init failed: org.freedesktop.DBus.Error.NoReply No reply within specified time
Apr 11 19:03:41 localhost dhcdbd: Failed to initialise D-Bus service. 
Apr 11 19:03:45 localhost anacron[4967]: Anacron 2.3 started on 2007-04-11
Apr 11 19:03:45 localhost anacron[4967]: Normal exit (0 jobs run)
Apr 11 19:03:45 localhost /usr/sbin/cron[4997]: (CRON) INFO (pidfile fd = 3)
Apr 11 19:03:45 localhost /usr/sbin/cron[4998]: (CRON) STARTUP (fork ok)
Apr 11 19:03:45 localhost /usr/sbin/cron[4998]: (CRON) INFO (Running @reboot jobs)
Apr 11 19:03:46 localhost vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 11 19:03:46 localhost vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 19:03:46 localhost vmnet-dhcpd: All rights reserved.
Apr 11 19:03:46 localhost vmnet-dhcpd: 
Apr 11 19:03:46 localhost vmnet-dhcpd: Please contribute if you find this software useful.
Apr 11 19:03:46 localhost vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 19:03:46 localhost vmnet-dhcpd: 
Apr 11 19:03:46 localhost vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 11 19:03:46 localhost vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 11 19:03:46 localhost vmnet-dhcpd: All rights reserved.
Apr 11 19:03:46 localhost vmnet-dhcpd: 
Apr 11 19:03:46 localhost vmnet-dhcpd: Please contribute if you find this software useful.
Apr 11 19:03:46 localhost vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Apr 11 19:03:46 localhost vmnet-dhcpd: 
Apr 11 19:03:47 localhost vmnet-dhcpd: Configured subnet: 172.16.220.0
Apr 11 19:03:47 localhost vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.220.254
Apr 11 19:03:47 localhost vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.220.0
Apr 11 19:03:47 localhost vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.220.0
Apr 11 19:03:47 localhost vmnet-dhcpd: Configured subnet: 172.16.74.0
Apr 11 19:03:47 localhost vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.74.254
Apr 11 19:03:47 localhost vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.74.0
Apr 11 19:03:47 localhost vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.74.0
Apr 11 19:04:34 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Apr 11 19:04:34 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Apr 11 19:04:34 localhost dhclient: All rights reserved.
Apr 11 19:04:34 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Apr 11 19:04:34 localhost dhclient: 
Apr 11 19:04:34 localhost dhclient: execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied
Apr 11 19:04:34 localhost dhclient: Listening on LPF/eth0/00:12:3f:18:bc:72
Apr 11 19:04:34 localhost dhclient: Sending on   LPF/eth0/00:12:3f:18:bc:72
Apr 11 19:04:34 localhost dhclient: Sending on   Socket/fallback
Apr 11 19:04:34 localhost dhclient: receive_packet failed on eth0: Network is down
Apr 11 19:04:38 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 11 19:04:38 localhost dhclient: send_packet: Network is down
Apr 11 19:04:42 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 11 19:04:42 localhost dhclient: send_packet: Network is down


List of files modified since the disaster.
Generated with ```
find / -mtime +2 -or -ctime +2 | grep -v ^/dev | grep -v ^/proc | grep -v ^/sys > /moddedfiles
```
> /
/etc
/etc/mtab
/etc/motd
/etc/printcap
/etc/lvm/.cache
/lib/modules/2.6.15-27-686/volatile
/lib/modules/2.6.15-27-686/volatile/nvidia_legacy.ko
/lib/modules/2.6.15-27-686/volatile/nvidia.ko
/lib/modules/2.6.15-27-686/volatile/new_ath_hal.ko
/lib/modules/2.6.15-27-686/volatile/fxusb.ko
/lib/modules/2.6.15-27-686/volatile/fglrx.ko
/lib/modules/2.6.15-27-686/volatile/fcusb.ko
/lib/modules/2.6.15-27-686/volatile/fcpcmcia_cs.ko
/lib/modules/2.6.15-27-686/volatile/fcpcmcia.ko
/lib/modules/2.6.15-27-686/volatile/fcpci.ko
/lib/modules/2.6.15-27-686/volatile/fcdslusba.ko
/lib/modules/2.6.15-27-686/volatile/fcdslusb2.ko
/lib/modules/2.6.15-27-686/volatile/fcdslusb.ko
/lib/modules/2.6.15-27-686/volatile/fcdslslusb.ko
/lib/modules/2.6.15-27-686/volatile/fcdslsl.ko
/lib/modules/2.6.15-27-686/volatile/fcdsl2.ko
/lib/modules/2.6.15-27-686/volatile/fcdsl.ko
/lib/modules/2.6.15-27-686/volatile/ath_hal.ko
/lib/modules/2.6.15-27-686/volatile/.mounted
/root/.lesshst
/usr/share/ppd/custom
/var/lib/urandom
/var/lib/urandom/random-seed
/var/lib/acpi-support/vbestate
/var/lib/acpi-support/system-manufacturer
/var/lib/acpi-support/system-product-name
/var/lib/acpi-support/system-version
/var/lib/acpi-support/bios-version
/var/lock
/var/lock/evms-engine
/var/lock/lvm
/var/log
/var/log/wtmp
/var/log/lastlog
/var/log/syslog
/var/log/auth.log
/var/log/evms-engine.log
/var/log/dmesg
/var/log/daemon.log
/var/log/user.log
/var/log/messages
/var/log/acpid
/var/log/cups/error_log
/var/log/evms-engine.1.log
/var/log/evms-engine.2.log
/var/log/evms-engine.3.log
/var/log/evms-engine.9.log
/var/log/evms-engine.4.log
/var/log/evms-engine.5.log
/var/log/evms-engine.6.log
/var/log/evms-engine.7.log
/var/log/evms-engine.8.log
/var/log/faillog
/var/log/udev
/var/run
/var/run/console
/var/run/console/jpkotta:2
/var/run/console/root:2
/var/run/console/root:1
/var/run/crond.reboot
/var/run/crond.pid
/var/run/mdadm.pid
/var/run/sshd.pid
/var/run/sshd
/var/run/laptop-mode-nolm-mountopts
/var/run/laptop-mode-state
/var/run/laptop-mode-enabled
/var/run/inetd.pid
/var/run/hotkey-setup
/var/run/gpm.pid
/var/run/cups
/var/run/cups/cupsd.pid
/var/run/cups/cups.sock
/var/run/cups/certs
/var/run/hal
/var/run/hal/hald.pid
/var/run/dbus
/var/run/dbus/pid
/var/run/dbus/system_bus_socket
/var/run/klogd
/var/run/klogd/kmsgpipe.pid
/var/run/klogd/kmsg
/var/run/syslogd.pid
/var/run/acpid.socket
/var/run/utmp
/var/run/screen
/var/run/dhclient.eth1.pid
/var/run/network
/var/run/network/ifstate
/var/run/resolvconf
/var/run/resolvconf/resolv.conf
/var/run/resolvconf/enable-updates
/var/run/resolvconf/interface
/var/run/resolvconf/interface/eth1.inet
/var/spool/postfix/etc/resolv.conf
/var/spool/postfix/maildrop
/var/spool/postfix/maildrop/230F7A08E0
/var/tmp/FAH502-Linux.exe-1.pid
/moddedfiles
/tmp
/tmp/.X11-unix
/tmp/.ICE-unix

/var/log/auth.log
> Apr 11 18:51:52 localhost sudo:  jpkotta : TTY=pts/1 ; PWD=/home/jpkotta/w/noip-2.1.4 ; USER=root ; COMMAND=/usr/bin/checkinstall
Apr 11 18:54:22 localhost gdm[4607]: (pam_unix) session closed for user jpkotta
Apr 11 18:55:47 localhost sshd[4872]: Server listening on 0.0.0.0 port 22.
Apr 11 18:56:04 localhost login[5271]: (pam_unix) session opened for user jpkotta by (uid=0)
Apr 11 18:56:05 localhost login[5298]: unable to cd to `/home/jpkotta' for user `jpkotta' 
Apr 11 18:56:05 localhost login[5271]: (pam_unix) session closed for user jpkotta
Apr 11 18:56:23 localhost login[5301]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=tty1 ruser= rhost=  user=root
Apr 11 18:56:26 localhost login[5301]: FAILED LOGIN (1) on `tty1' FOR `root', Authentication failure
Apr 11 18:56:36 localhost login[5301]: (pam_unix) session opened for user root by (uid=0)
Apr 11 18:56:36 localhost login[5308]: ROOT LOGIN  on `tty1'
Apr 11 18:57:23 localhost su[5375]: + tty1 root:jpkotta
Apr 11 18:57:23 localhost su[5375]: (pam_unix) session opened for user jpkotta by (uid=0)
Apr 11 19:00:18 localhost chsh[5432]: changed user `jpkotta' shell to `/bin/bash'
Apr 11 19:00:21 localhost su[5433]: + tty1 root:jpkotta
Apr 11 19:00:21 localhost su[5433]: (pam_unix) session opened for user jpkotta by (uid=0)
Apr 11 19:01:58 localhost sudo:     root : can't open /etc/sudoers: Permission denied ; TTY=tty1 ; PWD=/home/jpkotta ; USER=root ; COMMAND=/sbin/ifup eth1


**Research**

Some related threads:

[http://ubuntuforums.org/showthread.php?t=405942](http://ubuntuforums.org/showthread.php?t=405942)
[http://ubuntuforums.org/showthread.php?t=406895](http://ubuntuforums.org/showthread.php?t=406895)

**Plans**

I'm going to do some more tests, and then probably just install Feisty since it is so close to being released and I was going to update this month anyway.  I would *really* like to know what is going on.  If anyone has any ideas, I will not reinstall until we try them out.  This laptop is not essential for my work, but is inconvenient to have it not working.

---

### Post by adams0624 on 2007-04-14
Could anyone tell me how to enable the universe repo?  Thanks.

---

### Post by jpkotta on 2007-04-14
My problems were definately caused by noip's client and/or checkinstall.  I can reproduce the problem with a live CD.  

I boot the live CD (Xubuntu Dapper in this case), and do the following:
```
sudo aptitude install build-essential
sudo dpkg -i installwatch_0.6.3-2ubuntu1_i386.deb checkinstall_1.5.3-3ubuntu2_all.deb
tar zxvf noip-duc-linux.tar.gz
cd noip-2.1.4
make
sudo checkinstall
```

During checkinstall, I answer yes to the package docs question, then ctrl-C. Trying to run any command as the ubuntu user results in a permission error.  Permission is denied for /etc/sudoers, even as root.  Network is still up.

Edit:
The traditional "make install" causes no trouble.

---

### Post by jpkotta on 2007-04-30
It seems like this bug got fixed somewhere in the time between Dapper and Feisty.  I just tried to reproduce in Feisty under VMware, and it doesn't trash the system.  Clearly checkinstall has gone through some updates because it no longer depends upon installwatch.  Anyway, checkinstall still fails because it can't copy the binary or something like that, but make install still works.  

I suppose the lesson is be careful with checkinstall, which is too bad because I really like that program.  I've used it many times, but usually with programs using the GNU build system (./configure && make && make install), and this thing was definately not using that.  I think the problem was that it started asking questions.  

I'd still really like to know what the hell caused all the permission problems.

---

