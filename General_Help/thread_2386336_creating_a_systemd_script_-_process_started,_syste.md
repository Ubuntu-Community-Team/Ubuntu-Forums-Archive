---
title: "creating a systemd script - process started, systemd start hangs in terminal."
date: 2018-03-04
forum: General Help
---

### Post by derekcentrico on 2018-03-04
Okay, so I wanted a way to start this puppy automagically and figured this much out:

```
[Unit]
Description=transmission-daemon
After=syslog.target network.target


[Service]
Type=forking
PIDFile=/home/vpn/transmission-daemon.pid
User=vpn
StandardError=syslog
ExecStart=/usr/local/bin/transmission-daemon --config-dir  /home/vpn/.config/transmission-daemon/ -e /home/vpn/transmission.log --log-error 




[Install]
WantedBy=multi-user.target

```
The script started transmission.  However, it timed out eventually and killed the process.

```
root@homeserver:/lib/systemd/system# systemctl daemon-reload
root@homeserver:/lib/systemd/system# service transmission-daemon start
Job for transmission-daemon.service failed because a timeout was exceeded. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
root@homeserver:/lib/systemd/system# service transmission-daemon start

```

How can I get this script to finish starting and not kill off the underlying process?

Thanks to anyone who can help!

---

### Post by derekcentrico on 2018-03-04
My mistake entirely.  Solved it.

The ExtStart did not have the PID file generated.  Here's the final one in case someone is clumsy like me...

```
[Unit]
Description=transmission-daemon
After=syslog.target network.target


[Service]
Type=forking
PIDFile=/home/vpn/transmission-daemon.pid
User=vpn
StandardError=syslog
ExecStart=/usr/local/bin/transmission-daemon --config-dir  /home/vpn/.config/transmission-daemon/ -e /home/vpn/transmission.log --log-error  -x /home/vpn/transmission-daemon.pid
KillMode=process
WorkingDirectory=/home/vpn/


[Install]
WantedBy=multi-user.target

```

---

