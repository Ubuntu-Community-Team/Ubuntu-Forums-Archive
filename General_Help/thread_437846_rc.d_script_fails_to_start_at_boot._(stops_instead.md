---
title: "rc.d script fails to start at boot. (stops instead of starts)"
date: 2007-05-09
forum: General Help
---

### Post by nerbotuger on 2007-05-09
Hi, 
thought I'd post this rather peculiar problem of mine.

After a long night of configuring and installing various programs suddenly my sshd wouldn't start at boot.

At first I thought that the rc* links was broken so I did a "update-rc.d ssh remove" (or whatever the correct syntax is). And did a "update-rc.d ssh defaults".
Still no result.

The strange thing was that the startup script worked correctly, I could start it manually and all would be fine.

I then removed the rc* links again made a stripped down version of the script which I called mysshd:
```
#!/bin/bash

        case "$1" in
          start)
            echo "Starting the sshd"
            start-stop-daemon --start --exec /usr/sbin/sshd
                echo "Starting..." > /home/andreas/log
            ;;
          stop)
            echo "Stopping the sshd"
            start-stop-daemon --stop --exec /usr/sbin/sshd
                echo "stopping" > /home/andreas/log

            ;;
          restart)
            echo "Restarting the blahblahblah"
            $0 stop
            $0 start
            ;;
          *)
            echo "Usage: $0 {start|stop|restart}"
            ;;
        esac
```

Notice the high-tech debugging...
I then did a "update-rc.d mysshd defaults" and rebooted.
The thing that baffles me is when I do a cat of the logfile i created, it says "stopping"...

I'd really appreciate some feedback on this since I'm not that into the things that happens on boot.
Any advice on where to start looking?

If it helps, here's an output of "ls /etc/rc*/*mysshd"
/etc/rc0.d/K20mysshd  /etc/rc3.d/S20mysshd  /etc/rc6.d/K20mysshd
/etc/rc1.d/K20mysshd  /etc/rc4.d/S20mysshd
/etc/rc2.d/S20mysshd  /etc/rc5.d/S20mysshd

---

### Post by nerbotuger on 2007-05-09
Found out another thing. 

The reason why it logs "stopping" is because of it being linked in rc6.d and being called on reboot.

This means that the script does not start in any of the other runlevels...
*bump*

---

