---
title: "Need to restart upowerd on resume from suspend"
date: 2013-03-13
forum: General Help
---

### Post by Benjamindaines on 2013-03-13
There's a bug in upower that causes it to report inaccurate battery info sometimes after waking from sleep.  The workaround posted in the bug is to put a script in sleep.d that automatically restarts upowerd on wakeup.  However, when I put this script in (and add execute permissions) it doesn't work.  In fact it stops my network interfaces from waking up.  Any idea why and how to make it work?  Thanks. 

```
#!/bin/bash

case $1 in
  resume | thaw)
    UPOWERD=/usr/lib/upower/upowerd

    /usr/bin/killall -9 ${UPOWERD}
    ${UPOWERD} -d &
  ;;
esac
```

---

### Post by Nickolay Ihalainen on 2013-05-10
Hi Benjamindaines,

It looks like a race condition between network manager and wifi module reload after suspend or maybe upowerd if nm requires upowerd for some reason.
I have solved the problem by adding sleep before upowerd start. As an alternative you can restart network manager after upowerd start.
```
#!/bin/bash

case $1 in
  resume | thaw)
    /usr/local/bin/upowerd_restart &
  ;;
esac
```

 /usr/local/bin/upowerd_restart:
```
#!/bin/bash
sleep 20
UPOWERD=/usr/lib/upower/upowerd

/usr/bin/killall -9 ${UPOWERD}
exec ${UPOWERD} -d
```

---

