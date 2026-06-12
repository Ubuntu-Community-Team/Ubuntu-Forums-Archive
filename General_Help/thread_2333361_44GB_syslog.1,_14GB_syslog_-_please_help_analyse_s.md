---
title: "44GB syslog.1, 14GB syslog - please help analyse suspicious behaviour!"
date: 2016-08-09
forum: General Help
---

### Post by pete_hepple2 on 2016-08-09
I'm no expert so I've got by so far from tutorials, forum posts, etc, but this is something I really need help with. My syslogs have been huge recently, and I've only just noticed. Yesterday's begins like this:

```
Aug  8 07:44:13 Denork-Server gnome-session[3675]: ** (vino-server:3985): WARNING **: VNC authentication failure from '94.102.49.79'Aug  8 07:44:13 Denork-Server gnome-session[3675]: 08/08/2016 07:44:13 rfbAuthPasswordChecked: password check failed
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14 [IPv4] Got connection from client 94.102.49.79
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14   other clients:
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      94.102.49.79
Aug  8 07:44:14 Denork-Server gnome-session[3675]: message repeated 42 times: [ 08/08/2016 07:44:14      94.102.49.79]
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      105.100.142.82.static.b26.cz
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      94.102.49.79
Aug  8 07:44:14 Denork-Server gnome-session[3675]: message repeated 80 times: [ 08/08/2016 07:44:14      94.102.49.79]
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      61-69-81-238.syd.static-ipl.aapt.com.au
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      91.234.250.106
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: message repeated 84 times: [ 08/08/2016 07:44:14      no-reverse-dns-configured.com]
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: message repeated 2 times: [ 08/08/2016 07:44:14      93.174.93.240]
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: message repeated 2 times: [ 08/08/2016 07:44:14      93.174.93.240]
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      no-reverse-dns-configured.com
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
Aug  8 07:44:14 Denork-Server gnome-session[3675]: 08/08/2016 07:44:14      93.174.93.240
```

and carries on in pretty much the same way from what I can tell (I've seen references in other posts to a "tail" command that might help, so I'll try that later if neccessary.

Today's syslog begins in much the same way:

```
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11 [IPv4] Got connection from client 91.234.250.106Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11   other clients:
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      61-69-81-238.syd.static-ipl.aapt.com.au
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 243 times: [ 09/08/2016 07:45:11      94.102.49.79]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      91.234.250.106
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 147 times: [ 09/08/2016 07:45:11      94.102.49.79]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      113.207.27.194
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      113.207.27.194
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      91.234.250.106
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      61-69-81-238.syd.static-ipl.aapt.com.au
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      113.207.27.194
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      93.174.93.240
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 330 times: [ 09/08/2016 07:45:11      93.174.93.240]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      61-69-81-238.syd.static-ipl.aapt.com.au
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      93.174.93.240
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 373 times: [ 09/08/2016 07:45:11      93.174.93.240]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      61-69-81-238.syd.static-ipl.aapt.com.au
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      91.234.250.106
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      91.234.250.106
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 5 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      server.x79x.info
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 78 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      91.234.250.106
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 149 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 3 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 2 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      94.102.49.79
Aug  9 07:45:11 Denork-Server gnome-session[3675]: 09/08/2016 07:45:11      no-reverse-dns-configured.com
Aug  9 07:45:11 Denork-Server gnome-session[3675]: message repeated 6 times: [ 09/08/2016 07:45:11      no-reverse-dns-configured.com]
```

Is there anything obvious jumping out here? What should I be doing?

EDIT: Here's the last 100 lines:

```
Aug  9 18:00:19 Denork-Server org.gnome.zeitgeist.SimpleIndexer[3271]: ** (zeitgeist-fts:4571): WARNING **: Unable to get info on application://nautilus-autostart.desktopAug  9 18:00:19 Denork-Server gnome-session[3508]: (gedit:12888): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:19 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: Deferring authentication of '91.234.250.106' for 5 seconds
Aug  9 18:00:21 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:23 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:25 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: VNC authentication failure from '91.234.250.106'
Aug  9 18:00:25 Denork-Server gnome-session[3508]: 09/08/2016 18:00:25 rfbAuthPasswordChecked: password check failed
Aug  9 18:00:27 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:29 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:36 Denork-Server gnome-session[3508]: 09/08/2016 18:00:36 [IPv4] Got connection from client 91.234.250.106
Aug  9 18:00:36 Denork-Server gnome-session[3508]: 09/08/2016 18:00:36   other clients:
Aug  9 18:00:36 Denork-Server gnome-session[3508]: 09/08/2016 18:00:36      91.234.250.106
Aug  9 18:00:36 Denork-Server gnome-session[3508]: message repeated 8 times: [ 09/08/2016 18:00:36      91.234.250.106]
Aug  9 18:00:36 Denork-Server gnome-session[3508]: 09/08/2016 18:00:36 Client Protocol Version 3.3
Aug  9 18:00:36 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: Deferring authentication of '91.234.250.106' for 5 seconds
Aug  9 18:00:38 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:40 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:41 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: VNC authentication failure from '91.234.250.106'
Aug  9 18:00:41 Denork-Server gnome-session[3508]: 09/08/2016 18:00:41 rfbAuthPasswordChecked: password check failed
Aug  9 18:00:43 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:45 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:51 Denork-Server gnome-session[3508]: 09/08/2016 18:00:51 [IPv4] Got connection from client 91.234.250.106
Aug  9 18:00:51 Denork-Server gnome-session[3508]: 09/08/2016 18:00:51   other clients:
Aug  9 18:00:51 Denork-Server gnome-session[3508]: 09/08/2016 18:00:51      91.234.250.106
Aug  9 18:00:51 Denork-Server gnome-session[3508]: message repeated 9 times: [ 09/08/2016 18:00:51      91.234.250.106]
Aug  9 18:00:51 Denork-Server gnome-session[3508]: 09/08/2016 18:00:51 Client Protocol Version 3.3
Aug  9 18:00:52 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: Deferring authentication of '91.234.250.106' for 5 seconds
Aug  9 18:00:54 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:56 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:00:57 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: VNC authentication failure from '91.234.250.106'
Aug  9 18:00:57 Denork-Server gnome-session[3508]: 09/08/2016 18:00:57 rfbAuthPasswordChecked: password check failed
Aug  9 18:00:59 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:01 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:08 Denork-Server gnome-session[3508]: 09/08/2016 18:01:08 [IPv4] Got connection from client 91.234.250.106
Aug  9 18:01:08 Denork-Server gnome-session[3508]: 09/08/2016 18:01:08   other clients:
Aug  9 18:01:08 Denork-Server gnome-session[3508]: 09/08/2016 18:01:08      91.234.250.106
Aug  9 18:01:08 Denork-Server gnome-session[3508]: message repeated 10 times: [ 09/08/2016 18:01:08      91.234.250.106]
Aug  9 18:01:08 Denork-Server gnome-session[3508]: 09/08/2016 18:01:08 Client Protocol Version 3.3
Aug  9 18:01:08 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: Deferring authentication of '91.234.250.106' for 5 seconds
Aug  9 18:01:10 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:12 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:14 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: VNC authentication failure from '91.234.250.106'
Aug  9 18:01:14 Denork-Server gnome-session[3508]: 09/08/2016 18:01:14 rfbAuthPasswordChecked: password check failed
Aug  9 18:01:16 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:18 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:24 Denork-Server gnome-session[3508]: 09/08/2016 18:01:24 [IPv4] Got connection from client 91.234.250.106
Aug  9 18:01:24 Denork-Server gnome-session[3508]: 09/08/2016 18:01:24   other clients:
Aug  9 18:01:24 Denork-Server gnome-session[3508]: 09/08/2016 18:01:24      91.234.250.106
Aug  9 18:01:24 Denork-Server gnome-session[3508]: message repeated 11 times: [ 09/08/2016 18:01:24      91.234.250.106]
Aug  9 18:01:24 Denork-Server gnome-session[3508]: 09/08/2016 18:01:24 Client Protocol Version 3.3
Aug  9 18:01:24 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: Deferring authentication of '91.234.250.106' for 5 seconds
Aug  9 18:01:27 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:29 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:30 Denork-Server gnome-session[3508]: ** (vino-server:3840): WARNING **: VNC authentication failure from '91.234.250.106'
Aug  9 18:01:30 Denork-Server gnome-session[3508]: 09/08/2016 18:01:30 rfbAuthPasswordChecked: password check failed
Aug  9 18:01:32 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:34 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7105] device (enp2s0): state change: activated -> deactivating (reason 'user-requested') [100 110 39]
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7106] manager: NetworkManager state is now DISCONNECTING
Aug  9 18:01:48 Denork-Server whoopsie[2705]: [18:01:48] offline
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7144] audit: op="device-disconnect" interface="enp2s0" ifindex=2 pid=3845 uid=1000 result="success"
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7149] device (enp2s0): state change: deactivating -> disconnected (reason 'user-requested') [110 30 39]
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Withdrawing address record for fe80::d2d:4bbc:4d82:a3c on enp2s0.
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Leaving mDNS multicast group on interface enp2s0.IPv6 with address fe80::d2d:4bbc:4d82:a3c.
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Interface enp2s0.IPv6 no longer relevant for mDNS.
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: the GVariant format string '(u)' has a type of '(u)' but the given value has a type of '(a{sv})'
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: g_variant_get: assertion 'valid_format_string (format_string, TRUE, value)' failed
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7325] dhcp4 (enp2s0): canceled DHCP transaction, DHCP client pid 10412
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (deja-dup-monitor:6339): GLib-CRITICAL **: Source ID 88 was not found when attempting to remove it
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7325] dhcp4 (enp2s0): state changed bound -> done
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Withdrawing address record for 192.168.1.158 on enp2s0.
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7331] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Leaving mDNS multicast group on interface enp2s0.IPv4 with address 192.168.1.158.
Aug  9 18:01:48 Denork-Server avahi-daemon[2691]: Interface enp2s0.IPv4 no longer relevant for mDNS.
Aug  9 18:01:48 Denork-Server dnsmasq[10432]: setting upstream servers from DBus
Aug  9 18:01:48 Denork-Server org.gtk.vfs.Daemon[3271]: ** (process:4813): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  9 18:01:48 Denork-Server NetworkManager[2681]: <info>  [1470762108.7612] manager: NetworkManager state is now DISCONNECTED
Aug  9 18:01:48 Denork-Server dbus[2671]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: the GVariant format string '(u)' has a type of '(u)' but the given value has a type of '(a{sv})'
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: g_variant_get: assertion 'valid_format_string (format_string, TRUE, value)' failed
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: the GVariant format string '(u)' has a type of '(u)' but the given value has a type of '(a{sv})'
Aug  9 18:01:48 Denork-Server gnome-session[3508]: (vino-server:3840): GLib-CRITICAL **: g_variant_get: assertion 'valid_format_string (format_string, TRUE, value)' failed
Aug  9 18:01:48 Denork-Server systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug  9 18:01:48 Denork-Server dbus[2671]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  9 18:01:48 Denork-Server systemd[1]: Started Network Manager Script Dispatcher Service.
Aug  9 18:01:48 Denork-Server nm-dispatcher: req:1 'down' [enp2s0]: new request (1 scripts)
Aug  9 18:01:48 Denork-Server nm-dispatcher: req:1 'down' [enp2s0]: start running ordered scripts...
Aug  9 18:01:51 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:53 Denork-Server gnome-session[3508]: message repeated 2 times: [ (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied]
Aug  9 18:01:53 Denork-Server whoopsie[2705]: [18:01:53] Cannot reach: https://daisy.ubuntu.com
Aug  9 18:01:53 Denork-Server whoopsie[2705]: [18:01:53] Cannot reach: https://daisy.ubuntu.com
Aug  9 18:01:55 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:01:57 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:02:33 Denork-Server systemd[1]: Started CUPS Scheduler.
Aug  9 18:02:35 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:02:37 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied
Aug  9 18:04:34 Denork-Server systemd[1]: Starting Cleanup of Temporary Directories...
Aug  9 18:04:34 Denork-Server systemd-tmpfiles[15896]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Aug  9 18:04:34 Denork-Server systemd[1]: Started Cleanup of Temporary Directories.
Aug  9 18:04:37 Denork-Server gnome-session[3508]: (nautilus:3841): GVFS-WARNING **: can't init metadata tree /home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied

```

---

### Post by jamesisin on 2016-08-09
Looks like your mount point for your Samba share may not be permitted correctly:

"/home/petehepple/.local/share/gvfs-metadata/root: open: Permission denied"

Just one guess.  I know gvfs relates to Samba.

---

### Post by QIII on 2016-08-09
Are you allowing remote access to your computer?  You appear to be in the UK.

It appears that someone from the Czech Republic (or whose connection is coming out through an IP there) is making a pretty concerted effort to hack you via remote desktop.

It might be worth it to pull the plug from the web and get back to us from a different, secure, machine.

---

### Post by pete_hepple2 on 2016-08-09
> **QIII said:**
> Are you allowing remote access to your computer?  You appear to be in the UK.

It appears that someone from the Czech Republic (or whose connection is coming out through an IP there) is making a pretty concerted effort to hack you via remote desktop.

It might be worth it to pull the plug from the web and get back to us from a different, secure, machine.

That's what I was afraid of. I did try opening up the server so I could access it via VNC from work, but it never panned out - would it just be a simple case of disabling that? If so, is it any more complicated than disabling the port forwarding on my router?

---

### Post by QIII on 2016-08-09
Unfortunately, if this has been going on for some time and you are just now noticing, you may already be compromised.

How long ago did you open up remote desktop access and how far back do you have logs?

---

### Post by pete_hepple2 on 2016-08-09
Ah. I opened it up around 2 months ago. The oldest syslog I have is .7 from 3 Aug, and it begins in exactly the same way as the two above. What would you suggest I do?

---

### Post by QIII on 2016-08-09
Urm...

Do you have good backups?

:(

---

### Post by pete_hepple2 on 2016-08-09
Wow. That bad? What sort of damage could they have done?

I've run ```
gsettings set org.gnome.Vino network-interface lo
``` to prevent any further outside access via VNC which seems to have stopped the attempts, hopefully that should stop it for good.

---

### Post by QIII on 2016-08-09
An intruder might have done anything from minor to root-level.  You really can't be sure and you really can't trust a compromised machine again.  Your machine might be part of a botnet, your banking information may have been exposed, you may have a keylogger.  Who knows.

Things like VNC/remote desktop are some of the most frequent routes of compromise we deal with here.  Special care has to be taken with their use.

---

### Post by pete_hepple2 on 2016-08-24
Sorry for the slow reply, I've had a few other things I needed to deal with before getting back to this. I guess I'll have to start from scratch then, sadly. If I reinstall Ubuntu, will the other HDDs I have in LVM be affected at all?

---

