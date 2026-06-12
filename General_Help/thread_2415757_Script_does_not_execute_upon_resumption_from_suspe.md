---
title: "Script does not execute upon resumption from suspend"
date: 2019-03-31
forum: General Help
---

### Post by raleigh3 on 2019-03-31
This is in /etc/pm/sleep.d/.

Execute bit is set.

However it does not run?

```
#!/bin/sh

case "$1" in
suspend|hibernate)
    actions to
    take
    on suspend
    or hibernate
    ;;
resume|thaw)
    #other actions
    #to trigger
    #on resume
    gxmessage -fg red -font  'sans 30' -timeout 3  ' Computer has now resumed from suspend state.'
    ;;
esac
```

I found this in syslog.

```
Mar 31 02:00:51 7 dbus-daemon[932]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.95' (uid=0 pid=16760 comm="geany /etc/pm/sleep.d/On_Resume.sh " label="unconfined")
```

---

