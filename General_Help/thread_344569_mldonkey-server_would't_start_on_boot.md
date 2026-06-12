---
title: "mldonkey-server would't start on boot"
date: 2007-01-23
forum: General Help
---

### Post by ex-slacker on 2007-01-23
Hi everyone.

 sudo cat /etc/default/mldonkey-server

```

# MLDonkey configuration
# This file is loaded by /etc/init.d/mldonkey-server
# This file is managed using ucf(1)

MLDONKEY_DIR=/var/lib/mldonkey
MLDONKEY_USER=mldonkey
MLDONKEY_GROUP=mldonkey
MLDONKEY_UMASK=0022
MAX_ALIVE=48
LAUNCH_AT_STARTUP=true
MLDONKEY_NICENESS=0

```

I found in /var/log/messages only:

```

Jan 23 11:50:30 desktop mldonkey_server: Set niceness of the process: 0
Jan 23 11:50:30 desktop mldonkey_server: Set uid/gid of the process (114, 1001)
Jan 23 11:50:30 desktop mldonkey_server: Set umask of the process: 18

```

And no one process of mldonkey is running:
```

user@desktop:/etc/init.d$ ps ax | grep mlnet
 5093 pts/0    S+     0:00 grep mlnet

```

But it starts normal on manual request:
```

sudo /etc/init.d/mldonkey-server start

```

After that I have some modified  /etc/init.d/mldonkey-server
```

 start-stop-daemon --start --pidfile $PIDFILE \
    --exec $WRAPPER -- --start --daemon $WRAPPER_OPTIONS >> /root/ml.log 2>&1

```
I have just added a line
```

>> /root/ml.log 2>&1

```
to see what it is going.

After reboot i found in /root/ml.log:
```

 Could not guess $HOME environnement variable: provide a --chdir or $HOME

```

Than I have again added (before line of starting daemon) to /etc/init.d/mldonkey-server :
```

echo  "WRAPPER_OPTIONS are : $WRAPPER_OPTIONS"  >> /root/ml.log

```

And this is result:
```

WRAPPER_OPTIONS are :  --pidfile /var/run/mldonkey/mlnet.pid --chdir /var/lib/mldonkey --chgid mldonkey --umask 0022 --nice 0 --max-alive 48 --chuid mldonkey
 Could not guess $HOME environnement variable: provide a --chdir or $HOME

```

The option --chdir are provided.

:confused: 

Whats wrong, guys?

PS. ubuntu 6.10 mldonkey-server v2.8.1-1

---

### Post by ex-slacker on 2007-01-26
So, no linux experts here ...

---

