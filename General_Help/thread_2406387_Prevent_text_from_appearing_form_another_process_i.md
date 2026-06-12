---
title: "Prevent text from appearing form another process in a tty session"
date: 2018-11-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-11-20
see attached image
This is a real pita when you are trying to use nano

Related info:
```

chad@Z97Killer:~$ cat /etc/rc.local 
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
ct=$(mount -a | wc -l) # I have had systemd fail to mount stuff too many times and they need to be done in order, but does not care
if [ $ct -gt 0 ];then
    modprobe pcspkr
    sh -c "beep -f 500 -l 250 -r $ct;modprobe -r pcspkr" &
fi
if [ ! -d "/tmp/chad-Desktop" ];then # /tmp is a ram disk, i only store files temporary in my desktop folder (i like a clean desktop)
    mkdir  /tmp/chad-Desktop
    chown chad:chad /tmp/chad-Desktop
    chmod 1750 /tmp/chad-Desktop
    if [ -d "/home/chad/Desktop" ];then
        mount --bind /tmp/chad-Desktop /home/chad/Desktop
    fi
    mkdir /tmp/thermal
    chmod 777 /tmp/thermal
fi
if [ $(pgrep -f ff32FanCtrl.py | wc -l) -eq 0 ];then
    /usr/local/bin/ff32FanCtrl.py &
fi
exit 0
```

---

### Post by TheFu on 2018-11-20
Whenever you start any programs from the same terminal, redirect the stderr and stdout to somewhere else, not the defaults.  Controlling stdout and stderr is a common task.

---

