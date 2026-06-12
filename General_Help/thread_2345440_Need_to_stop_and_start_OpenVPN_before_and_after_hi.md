---
title: "Need to stop and start OpenVPN before and after hibernate/wakeup"
date: 2016-12-04
forum: General Help
---

### Post by testik on 2016-12-04
Hello!

I need to stop OpenVPN before hibernate and start after wake up on Lubuntu 16.04

I've made this script:
```

#!/bin/sh


case "$1" in
        resume)
                service openvpn start
                ;;
        thaw)
                service openvpn start
                ;;
        suspend)
                service openvpn stop
                ;;
        hibernate)
                service openvpn stop
                ;;
esac

```
and put it in /etc/pm/sleep.d . But this doesnt work.

---

