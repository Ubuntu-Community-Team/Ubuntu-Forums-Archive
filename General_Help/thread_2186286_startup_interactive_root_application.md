---
title: "startup interactive root application"
date: 2013-11-06
forum: General Help
---

### Post by joaoneves792 on 2013-11-06
The other day i wrote a program that needs root privileges (to listen on port 67) that basically creates a system notification every time someone connects to my network. This all works very well but now i wanted it to start automatically, so i created a script in /etc/init.d to start it at startup. The program is executed just fine, the only problem is i don't get any notifications when someone connects to the network. Below is the script i put in /etc/init.d. Could someone tell me why it is not showing the notifications, or a better way to start this program at startup?

```
#!/bin/bash


### BEGIN INIT INFO
# Provides:          dhcpmonitor
# Required-Start:    $all
# Required-Stop:     
# Default-Start:     5 
# Default-Stop:      0 1 2 3 4
# Short-Description: Start DHCPMonitor at boot time
# Description:       start the DHCPmon.
# X-Interactive:     true
### END INIT INFO


/bin/DHCPmon&

```

---

