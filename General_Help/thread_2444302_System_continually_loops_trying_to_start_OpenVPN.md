---
title: "System continually loops trying to start OpenVPN"
date: 2020-05-28
forum: General Help
---

### Post by hans12345 on 2020-05-28
My wife's desktop has a loop involving OpenVPN. Which seems strange since she does not even know what a VPN is !

She runs 18.04 LTS.

The system tries continually to start OpenVPN and fails again and again.

Here is a section of the log:

```

May 28 00:08:28 Ace rsyslogd:  [origin software="rsyslogd" swVersion="8.32.0" x-pid="1068" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:28 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:28 Ace systemd[1]: openvpn@client.service: Service hold-off time over, scheduling restart.
May 28 00:08:28 Ace systemd[1]: openvpn@client.service: Scheduled restart job, restart counter is at 6997.
May 28 00:08:28 Ace systemd[1]: Stopped OpenVPN connection to client.
May 28 00:08:28 Ace systemd[1]: Starting OpenVPN connection to client...
May 28 00:08:28 Ace ovpn-client[31131]: Options error: --ca fails with 'ca.crt': No such file or directory (errno=2)
May 28 00:08:28 Ace ovpn-client[31131]: Options error: --cert fails with 'client.crt': No such file or directory (errno=2)
May 28 00:08:28 Ace ovpn-client[31131]: WARNING: cannot stat file 'client.key': No such file or directory (errno=2)
May 28 00:08:28 Ace ovpn-client[31131]: Options error: --key fails with 'client.key': No such file or directory (errno=2)
May 28 00:08:28 Ace ovpn-client[31131]: Options error: Please correct these errors.
May 28 00:08:28 Ace ovpn-client[31131]: Use --help for more information.
May 28 00:08:28 Ace systemd[1]: openvpn@client.service: Main process exited, code=exited, status=1/FAILURE
May 28 00:08:28 Ace systemd[1]: openvpn@client.service: Failed with result 'exit-code'.
May 28 00:08:28 Ace systemd[1]: Failed to start OpenVPN connection to client.
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:29 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:30 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:31 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:32 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
May 28 00:08:33 Ace gnome-shell[2092]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
May 28 00:08:34 Ace systemd[1]: openvpn@client.service: Service hold-off time over, scheduling restart.
May 28 00:08:34 Ace systemd[1]: openvpn@client.service: Scheduled restart job, restart counter is at 6998.
May 28 00:08:34 Ace systemd[1]: Stopped OpenVPN connection to client.
May 28 00:08:34 Ace systemd[1]: Starting OpenVPN connection to client...
May 28 00:08:34 Ace ovpn-client[31140]: Options error: --ca fails with 'ca.crt': No such file or directory (errno=2)
May 28 00:08:34 Ace ovpn-client[31140]: Options error: --cert fails with 'client.crt': No such file or directory (errno=2)
May 28 00:08:34 Ace ovpn-client[31140]: WARNING: cannot stat file 'client.key': No such file or directory (errno=2)
May 28 00:08:34 Ace ovpn-client[31140]: Options error: --key fails with 'client.key': No such file or directory (errno=2)
May 28 00:08:34 Ace ovpn-client[31140]: Options error: Please correct these errors.
May 28 00:08:34 Ace ovpn-client[31140]: Use --help for more information.
May 28 00:08:34 Ace systemd[1]: openvpn@client.service: Main process exited, code=exited, status=1/FAILURE
May 28 00:08:34 Ace systemd[1]: openvpn@client.service: Failed with result 'exit-code'.
May 28 00:08:34 Ace systemd[1]: Failed to start OpenVPN connection to client.

```

Questions:
-what is going on?
- is there any reason why the system is trying to start OpenVPN without the user asking for it?
- has she been hacked?
- what are my next steps - I could upgrade to 20.04 LTS, or if this is a sign of Malware, I should do a clean install?

Thanks for any help

---

### Post by dino99 on 2020-05-28
The issue is about certificates upgrades, which fail; then there is loop for retrying.
The easiest/fastest way is to purge then reinstall 'ca-certificates' and 'ca-certificates-java' , either from command line or better from synaptic

A smoother way is to simply do 'sudo dpkg-reconfigure ca-certificates'

---

### Post by hans12345 on 2020-05-30
Thanks Dino99

I was worried about OpenVPN was being accessed.

I decided to remove OpenVPN with Synaptics. That worked for the OpenVPN part of the loop.

But not the ayatana part.

I looked around and found that this is a known open bug. I looked in the comments and found that removing the multiload would prevent that part of the loop.

So I removed multiload and the problem has gone.

---

### Post by dino99 on 2020-05-30
Maybe you can share with us the related bug number/link and how you get ride of the multiload loop (might help others hitting the same related problem)

---

