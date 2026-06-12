---
title: "boot error /etc/rc.local is not created"
date: 2016-05-05
forum: General Help
---

### Post by Sherman_Willden on 2016-05-05
I upgraded to 16.04. /var/log/boot.log has the following two errors listed:

[[   29.049975] rc.local[654]: /etc/rc.local: 14: /etc/rc.local: SETPCI: not found
FAILED] Failed to start /etc/rc.local Compatibility.
See 'systemctl status rc-local.service' for details.

How important is this? When I perform systemctl --all I see several 'not found' items.

Thank you;

Sherman

---

### Post by matt_symes on 2016-05-05
Hi

Can you post the contents of your rc.local file.

Kind regards

---

### Post by Sherman_Willden on 2016-05-06
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

SETPCI -S 00:02.0 f4.b-0

exit 0

```

And here is a copy of the not found services:
 tmp.mount
&#9679; auditd.service
&#9679; cloud-init.service
&#9679; festival.service
  getty-static.service
&#9679; keyboard-setup.service
&#9679; snapd.firstboot.service
&#9679; systemd-sysusers.service
&#9679; systemd-update-done.service
&#9679; systemd-vconsole-setup.service
&#9679; syslog.target



Thank you;

Sherman

---

### Post by matt_symes on 2016-05-06
Hi

The line below is why rc.local is failing. 

> SETPCI -S 00:02.0 f4.b-0

It's not a valid command. There is the command

```
setpci
```

Notice the lower case ? Linux is case sensitive.

My next question would be why was that line added to rc.local ?

It either needs to be lower case or removed but that can only be determined when you answer the above question.

Kind regards

---

