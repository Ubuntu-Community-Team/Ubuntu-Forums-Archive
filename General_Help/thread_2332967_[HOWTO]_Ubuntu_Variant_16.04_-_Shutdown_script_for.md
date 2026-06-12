---
title: "[HOWTO] Ubuntu Variant 16.04 - Shutdown script for SYSTEMD"
date: 2016-08-05
forum: General Help
---

### Post by smartmagnet on 2016-08-05
This shutdown script is an inversion of the startup script /etc/rc.local

Source Reference:  [http://forums.fedoraforum.org/showthread.php?t=301243](http://forums.fedoraforum.org/showthread.php?t=301243)

Create SYSTEMD configuration file

```
cat >/lib/systemd/system/SHUTDOWN.service
[Unit]
Description=/etc/rc.local.shutdown Compatibility
Before=shutdown.target
[Service]
ExecStart=/bin/true
ExecStop=/etc/RC-LOCAL-SHUTDOWN
RemainAfterExit=yes
[Install]
WantedBy=multi-user.target
```

Create local shutdown script.
Note: Name of the file is derived for 'ExecStop' example above, but the name can be anything you desire.

```
cat >/etc/RC-LOCAL-SHUTDOWN
#!/bin/bash
# Enter whatever script commands here.
# Example: date >/home/user/TODAYDATE.TXT
```

```
chmod -v 755 /etc/RC-LOCAL-SHUTDOWN
```

```
systemctl start RC-LOCAL-SHUTDOWN
```

```
systemctl enable RC-LOCAL-SHUTDOWN
```

---

