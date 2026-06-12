---
title: "How I got spamassassin to work"
date: 2008-02-02
forum: General Help
---

### Post by janarene on 2008-02-02
Spam Assassin seemed to install properly using Synaptic and apt-get but refused to start, complaing of a port already in use:

```
could not create INET socket on 127.0.0.1:783: Address already in use
```

if you look for the spamd process, you probably have 2 of them running titled 'spamd child'.  Go ahead and kill those off.

```
root@cricket:/etc/init.d# ps aux | grep spamd
spamd    11059  0.0  3.3  37316 34260 ?        S    10:28   0:02 spamd child
spamd    11060  0.0  3.0  35280 31424 ?        S    10:28   0:00 spamd child

root@cricket:/etc/init.d# killall spamd


```

Take a look for the spamassassin home directory, it's supposed to be at /var/lib/spamassassin.  Mine was missing.

```
mkdir /var/lib/spamassassin 

```
and I thought it would be a good idea to:
```

chown spamd /var/lib/spamassin
```

Edit your /etc/default/spamassassin. file.  Look for the commented PIDFILE= line at the bottom.  That needs to be uncommented and pointing to a directory the user 'spamd' can write to so it can make the .PID file.  I just made a /home/spamd directory and set the permissions.

*editing the /etc/default/spamassassin file*
```
# Pid file
# Where should spamd write its PID to file? If you use the -u or
# --username option above, this needs to be writable by that user.
# Otherwise, the init script will not be able to shut spamd down.
PIDFILE="/home/spamd/spamd.pid"
```

*creating the directory for the .pid file*
```
md /home/spamd
chown spamd /home/spamd
```

Start it up and stand back
```
/etc/init.d/spamassassin start
```


And now I get a start without any error messages and am able to configure the configuration with webmin.  Now when webmin restarts the daemon, it seems to do so cleanly.

(please no comments about how I refuse to use the sudo command)

---

